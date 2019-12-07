# Colecciones
Existen dos formas de agrupar objetos: mediante la creación de matrices de objetos y mediante la creación de colecciones de objetos.
Las matrices son muy útiles para crear y trabajar con un número fijo de objetos fuertemente tipados.
Las colecciones proporcionan un método más flexible para trabajar con grupos de objetos.
A diferencia de las matrices, el grupo de objetos con el que trabaja puede aumentar y reducirse dinámicamente a medida que cambian las necesidades de la aplicación.

![List](https://github.com/dev-Niko/tla/blob/master/list.png)

•Una colección es una clase, de modo que antes de poder agregar elementos a una nueva colección, debe declararla.
•Una colección genérica cumple la seguridad de tipos para que ningún otro tipo de datos se pueda agregar a ella.
•Cuando se recupera un elemento de una colección genérica, no tiene que determinar su tipo de datos ni convertirlo.

   
List<int> intList = new List<int>();

//Or

IList<int> intList = new List<int>();
```
    

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTk2Mjc2MjgzMSwtNzM4NzA0NTU1XX0=
-->