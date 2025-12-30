
### 5. Algoritmo mental para encarar este tipo de ejercicios

Cuando te den un esquema gigante como este:

1. **Separá entidades claras**: ¿qué cosas existen solas? (pozo, parámetro, operario, instrumento, vehículo, medición).
    
2. **Anotá dependencias funcionales directas**: cada entidad se describe con sus atributos propios.
    
3. **Detectá relaciones N:M**: medición–parámetro, medición–instrumento, medición–vehículo.
    
4. **Definí claves candidatas** en el esquema desnormalizado (normalmente es una mega-clave compuesta de todas las relaciones).
    
5. **Normalizá**: cada entidad → su tabla, cada N:M → tabla intermedia, hasta llegar a 4FN


