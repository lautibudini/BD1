

**PATIENT** (patient_id , patient_name, patient_address, patient_city, primary_phone, secondary_phone)
**DOCTOR**  (doctor_id, doctor_name, doctor_address, doctor_city, doctor_speciality)
**APPOINTMENT** (patient_id, appointment_date, appointment_duration, contact_phone, observations, payment_card)
**MEDICAL_REVIEW** (patient_id, appointment_date, doctor_id)
**PRESCRIBED_MEDICATION** (patient_id, appointment_date, medication_name)

CP = (patient_id, doctor_id, appointment_date,  medication_name)


## Ejercicio 2

Hallar aquellos pacientes que para todas sus consultas médicas siempre hayan dejado su número de teléfono primario (nunca el teléfono secundario).

```c
SELECT p.patient_id, p.patient_name
FROM PATIENT p
WHERE NOT EXISTS(
		SELECT *
		FROM APPOINTMENT a
		WHERE a.patient_id = p.patient_id AND a.contact_phone <> primary_phone
)
```

## Ejercicio 3 

Crear una vista llamada ‘doctors_per_patients’ que muestre los id de los pacientes y los id de doctores de la ciudad donde vive el paciente.

```c
CREATE VIEW doctors_per_patients AS
SELECT p.patient_id, d.doctor_id
FROM PATIENT p JOIN DOCTOR d ON p.patient_city = d.doctor_city
```

## Ejercicio 4

Utiliza la vista generada en el ejercicio anterior para resolver las siguientes consultas:
- Obtener la cantidad de doctores por cada paciente que tiene disponible en su ciudad
- Obtener los nombres de los pacientes sin doctores en su ciudad
- Obtener los doctores que comparten ciudad con más de cinco pacientes.

```c
SELECT p.patient_id , COUNT(p.doctor_id) AS cantDoctores
FROM doctors_per_patients p
GROUP BY p.patient_id; 
```

```c
SELECT p.patient_name, p.patient_id
FROM Patient p 
WHERE p.patient_id NOT IN (
	SELECT dp.patient_id
	FROM doctors_per_patients dp
)
```

```c
SELECT dp.doctor_id , COUNT( DISTINCT dp.doctor_id) AS cantidadComparte
FROM doctors_per_patients dp
GROUP BY dp.doctor_id
HAVING COUNT(DISTINCT dp.doctor_id ) > 5
```
> Uso el DISTINCT por si hay alguna columna repetida.


## Ejercicio 5

Escribe y ejecute la sentencia correspondiente para crear la siguiente tabla:

**APPOINTMENTS_PER_PATIENT**  
**idApP**: int(11) PK AI  
**id_patient**: int(11)  
**count_appointments**: int(11)  
**last_update**: datetime  
**user**: varchar(16)

```c
CREATE TABLE appointments_per_patient(
	idApP INT(11) PRIMARY KEY AUTO_INCREMENT, 
	id_patient INT(11), 
	count_appointments INT(11),
	last_update DATETIME,
	user VARCHAR(16),
)
```


## Ejercicio 6 

Crear un Stored Procedure que realice los siguientes pasos dentro de una transacción:

a) Realizar la siguiente consulta: cada _pacient_ (identificado por _id_patient_), calcule la cantidad de appointments que tiene registradas. Registrar la fecha en la que se realiza esta carga y además del usuario con el se realiza.
b) Guardar el resultado de la consulta en un cursor.
c) Iterar el cursor e insertar los valores correspondientes en la tabla APPOINTMENTS PER PATIENT. Tenga en cuenta que last_update es la fecha en que se realiza esta carga, es decir la fecha actual, mientras que user es el usuario logueado actualmente, utilizar las correspondientes funciones para esto.

```c
// A 

//DELIMITER
CREATE PROCEDURE ejercicio_a()
BEGIN

	START TRANSACTION; 
		
	INSERT INTO APPOINTMENTS_PER_PATIENT (
			patient_id, 
			cantidad, 
			last_update, 
			user
	)
	SELECT 
			p.patient_id , 
			COUNT(a.patient_id) AS cantidad, 
			last_update() AS last_update, 
			user() AS user
	FROM Patient p LEFT JOIN appointment a ON p.patient_id = a.patient_id
	GROUP BY p.patient_id; 
	
	COMMIT; 

END//
DELIMITER; 
```

```c
// B

// Acá declaramos las variables que usaremos luego en el cursor
DECLARE done INT DEFAULT 0; //Variable que usaremos para cortar. 
DECLARE c_patient_id INT;
DECLARE c_cantidad INT; 

DECLARE ejercicio_b CURSOR FOR
	SELECT p.patient_id, COUNT(a.patient_id) AS cantidad
	FROM Patient p LEFT JOIN appointment a ON p.patient_id = a.patient_id
	GRUOUP BY p.patient_id

// Cuando ya no hay más filas, el FETCH dispara “NOT FOUND” y pone done = 1.
DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = 1;

```

```c

// C 

DELIMITER //
CREATE PROCEDURE ejercicio_c()
BEGIN

CALL procedimiento_b(); //????????????

//Inicia la transacción
START TRANSACTION;


OPEN ejercicio_b;
 
read_loop: LOOP
	FETCH ejercicio_b INTO c_patient_id, c_cantidad; //Trae una fila
	IF done THEN
		LEAVE read_loop; //Salimos del loop cuando no hay más filas
	END IF; 
	
	//Insertarmos los valores a la tabla nueva
	INSERT INTO APPOINTMENTS_PER_PATIENT (patient_id, cantidad_appointments, last_update, user)
	VALUES (v_patient_id, v_cantidad, last_update(), user());
END LOOP; 
	
CLOSE ejercicio_b; 

//Confirma la transacción
COMMIT;

END //
DELIMITER ;

```

## Ejercicio 7

Indique si las siguientes afirmaciones sobre triggers son verdaderas o falsas. Justifique las falsas.
1. Un trigger se ejecuta únicamente cuando se inserta una fila en una tabla.
2. Un trigger puede ejecutarse antes o después de la operación, esto es definido automáticamente según el tipo de la operación (UPDATE, INSERT o DELETE)
3. Todo trigger debe asociarse a una tabla en concreto.
4. NEW y OLD son palabras clave que permiten acceder a los valores de las filas afectadas y se pueden usar ambos independientemente de la operación utilizada.
5. FOR EACH ROW en un trigger se usa para indicar que el trigger se ejecutará una vez por cada fila afectada por la operación.
   
Respuesta : 
1. Falsa, El trigger es ejecutado dependiendo de como este configurado puede ser Antes o Después de Insertar, Eliminar o Modificar una fila.
2. Falsa, Nosotros somos los que decidimos si se hace antes o después
3. Verdadera, ya que los triggers actúan o se disparan segun las operaciones que se hagan sobre una tabla. 
4. Falsa, la operación de NEW esta  disponible para INSERT y UPDATE (apuntando al nuevo valor), OLD esta disponible el las operaciones UPDATE y DELETE (apuntando al valor antiguo). No se pueden usar ambos en cualquier operación. 
5. Verdadero, ya que esto permite que el trigger procese cada fila individualmente cuando una operación afecta varias filas. 

## Ejercicio 8 

Crear un Trigger de modo que al insertar un dato en la tabla Appointment, se actualice la cantidad de appointments del paciente, la fecha de actualización y el usuario responsable de la misma (actualiza la tabla APPOINTMENTS PER PATIENT).

Respuesta : 

```c

DELIMITER//
CREATE TRIGGER ejercicio8
AFTER INSERT ON Appointment
FOR EACH ROW
BEGIN
	UPDATE appointments_per_patient
	SET cantidad = (
		SELECT COUNT(*)
		FROM appointment 
		GRUOP BY patient_id = NEW.patient_id
	), 
	last_update = NOW(), 
	user = USER()
	WHERE patient_id = NEW.patient_id; 
END//
DELIMITER; 
```

## Ejercicio 9  

Crear un stored procedure que sirva para agregar un _appointment_, junto el registro de un doctor que lo atendió (_medical_review_) y un medicamento que se le recetó (_prescribed_medication_), dentro de una sola transacción. El stored procedure debe recibir los siguientes parámetros: patient_id, doctor_id, appointment_duration, contact_phone, appointment_address, medication_name. El appointment_date será la fecha actual. Los atributos restantes deben ser obtenidos de la tabla Patient (o dejarse en NULL).

Respuesta : 

```c

DELIMITER//
CREATE PROCEDURE ejercicio9(IN p_patient_id INT, IN p_doctor_id INT, IN p_appointment_duration INT,IN p_contact_phone VARCHAR(20),IN p_appointment_address VARCHAR(100), IN p_medication_name VARCHAR(100) )
BEGIN

DECLARE fecha DATETIME DEFAULT last_update()

START TRANSACTION; 

//appointment
INSERT INTO Appointment(patient_id, appointment_date, appointment_duration, contact_phone, observations, payment_card)
VALUES(p_patient_id, fecha, p_appointment_duration, p_contact_phone, NULL, NULL);

//medical_review
INSERT INTO medical_review(patient_id, appointment_date, doctor_id)
VALUES(p_patient_id, fecha, p_doctor_id);

//prescribed_medication
INSERT INTO prescribed_medication(patient_id, appointment_date, medication_name)
VALUES(p_patient_id, fecha, p_medication_name);


COMMIT; 

END//
DELIMITER; 

```


## Ejercicio 10

Ejecutar el stored procedure del punto 9 con los siguientes datos:  
    patient_id: 10004427  
    doctor_id: 1003  
    appointment_duration: 30  
    contact_phone: +54 15 2913 9963  
    appointment_address: ‘Hospital Italiano’  
    medication_name: ‘Paracetamol’

Respuesta : 

```c
CALL ejercicio9(
    10004427,           
    1003,               
    30,                 
    '+54 15 2913 9963', 
    'Hospital Italiano',
    'Paracetamol'       
);
```

