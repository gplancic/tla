# Colecciones

Existen dos formas de agrupar objetos: mediante la creación de matrices de objetos y mediante la creación de colecciones de objetos.

Las matrices son muy útiles para crear y trabajar con un número fijo de objetos fuertemente tipados.
Las colecciones proporcionan un método más flexible para trabajar con grupos de objetos.
A diferencia de las matrices, el grupo de objetos con el que trabaja puede aumentar y reducirse dinámicamente a medida que cambian las necesidades de la aplicación.

![List](https://github.com/dev-Niko/tla/blob/master/list.png)

•Una colección es una clase, de modo que antes de poder agregar    elementos a una nueva colección, debe declararla. 
•Una colección    genérica cumple la seguridad de tipos para que ningún otro tipo de    datos se pueda agregar a ella. 
•Cuando se recupera un elemento de una    colección genérica, no tiene que determinar su tipo de datos ni    convertirlo.

Instaciación de una colección:

    List<int> intList = new List<int>();
    
   
 La siguiente tabla enumera las propiedades y métodos importantes de la clase List <T>:
    
|Método| Uso |
|--|--|
| True |Agrega un elemento al final de una Lista <T>.  |
||Agrega elementos de la colección especificada al final de una Lista <T>.|
|  | Busca el elemento y devuelve un índice del elemento. |
|  | Elimina todos los elementos de una Lista <T>. |
|  | Comprueba si el elemento especificado existe o no en una Lista <T>. |
|  | Encuentra el primer elemento basado en la función de predicado especificada. |
|  | Itera a través de una Lista <T>. |
|  | Inserta un elemento en el índice especificado en una Lista <T>. |
|  | Inserta elementos de otra colección en el índice especificado. |
|  | Elimina la primera ocurrencia del elemento especificado. |
|  | Elimina el elemento en el índice especificado. |
|  | Elimina todos los elementos que coinciden con la función de predicado proporcionada. |
|  | Ordena todos los elementos. |
|  | Establece la capacidad al número real de elementos. |
|  | Determina si cada elemento de la Lista <T> coincide con las condiciones definidas por el predicado especificado. |
||||


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwNTUzNDQ1NTUsLTczODcwNDU1NV19
-->