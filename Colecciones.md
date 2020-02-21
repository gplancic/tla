# Colecciones en C#

Muchas aplicaciones requieren agrupar objetos por ejemplo una agenda un   
 catálogo de productos o el mismo sistema de alumnos de la Universidad. 

El número de elementos a agrupar varía por lo que 2 operaciones comunes a realizar son la adición y eliminacide elementos  
 - Eliminación de elementos
 
Y hay que ser capaces de manipular los elementos de la colección
 - Búsqueda de elementos  
 - Consulta y modificación de elementos

Hay dos formas de agrupar objetos: 
 - **Matrices**
 - **Colecciones** 

Las matrices son muy útiles para crear y trabajar con un número fijo de objetos fuertemente tipados.

Las colecciones proporcionan un método más flexible para trabajar con grupos de objetos.

# Tipos de colecciones

.NET Framework proporciona muchas colecciones comunes.  Cada tipo de colección está diseñado para un fin específico.

En esta sección se describen algunas de las clases de colecciones comunes:

-   Clases System.Collections.Generic
    
-   Clases  System.Collections.Concurrent
    
-   Clases  System.Collections

# Colecciones genéricas

Veamos una categoría de colección llamada Colecciones genéricas. Sabemos qué es una colección en términos generales; Es un objeto que contiene un grupo de otros objetos y puede ser trabajado o procesado de alguna manera. Intentemos definir qué queremos decir con genérico.

Lo que esto significa es que podemos diseñar una clase que recibirá parámetros, los tipos de estos parámetros se definen cuando se crea una instancia de un objeto de clase genérico.

Entonces, en el caso de una colección genérica, podemos crear una instancia de una lista que solo contiene cadenas. No se pueden agregar elementos de lista que no sean cadenas. Entonces podríamos definir otra Lista que solo acepte entradas, y así sucesivamente. De esta manera, podemos diseñar clases que se puedan reutilizar en muchos contextos diferentes, y aumentar la seguridad de los tipos también.

Es fácil ver por qué los tipos de colección son candidatos ideales para el comportamiento genérico. Una colección es un contenedor, como una bolsa, por ejemplo. Probablemente no querríamos ir a la tienda y comprar varias bolsas, solo porque podríamos ponerles diferentes cosas en diferentes momentos. Probablemente solo compraríamos una bolsa y aceptaremos que podemos usarla para transportar diferentes tipos de objetos cuando sea necesario.

Entonces, por ejemplo, podríamos crear una clase de colección genérica que nos permita mantener cadenas en un punto de nuestro código, y mantener entradas en otro punto, en lugar de crear dos clases, una para contener solo cadenas y otra para contener entradas.

# Tipos de colecciones genéricas

Tenga en cuenta que todos estos tipos se encuentran dentro del espacio de nombres System.Collections.Generic e implementan la interfaz ICollection.

El punto relevante aquí es que al implementar ICollection, se proporcionan algunos métodos y propiedades estándar como Agregar, Contiene y Eliminar que hacen que el manejo de colecciones sea muy intuitivo.
Instaciación de una colección:

    List<int> intList = new List<int>();
    
   
 La siguiente tabla enumera las propiedades y métodos importantes de la clase List< T > :
    
|Método| Uso |
|--|--|
| Add |Agrega un elemento al final de una Lista <T>.  |
|AddRange|Agrega elementos de la colección especificada al final de una Lista <T>.|
| BinarySearch | Busca el elemento y devuelve un índice del elemento. |
| Clear | Elimina todos los elementos de una Lista <T>. |
| Contains | Comprueba si el elemento especificado existe o no en una Lista <T>. |
| Find | Encuentra el primer elemento basado en la función de predicado especificada. |
|Foreach| Itera a través de una Lista <T>. |
| Insert | Inserta un elemento en el índice especificado en una Lista <T>. |
|  InsertRange| Inserta elementos de otra colección en el índice especificado. |
| Remove | Elimina la primera ocurrencia del elemento especificado. |
| RemoveAt | Elimina el elemento en el índice especificado. |
| RemoveRange | Elimina todos los elementos que coinciden con la función de predicado proporcionada. |
| Sort | Ordena todos los elementos. |
| TrimExcess | Establece la capacidad al número real de elementos. |
| TrueForAll | Determina si cada elemento de la Lista <T> coincide con las condiciones definidas por el predicado especificado. |
||||

**Ejemplo agregar elementos utilizando a una colección utilizando *ADD***

    using System;
    using System.Collections.Generic;
    
    public class Program
    {
    	public static void Main()
    	{
    		IList<int> intList = new List<int>();
    		intList.Add(10);
    		intList.Add(20);
    		intList.Add(30);
    		intList.Add(40);
    		
    		Console.WriteLine(intList.Count);
    		
    		IList<string> strList = new List<string>();
    		strList.Add("one");
    		strList.Add("two");
    		strList.Add("three");
    		strList.Add("four");
    		strList.Add("four");
    		strList.Add(null);
    		strList.Add(null);
    		
    		Console.WriteLine(strList.Count);
    		
    		IList<Student> studentList = new List<Student>();
    		studentList.Add(new Student());
    		studentList.Add(new Student());
    		studentList.Add(new Student());
    		
    		Console.WriteLine(studentList.Count);
    		
    	}
    }

**Resultado:**

    4  
    7  
    3

**Agregar objetos a una colección**
    
    using System;
    using System.Collections.Generic;
    public class Program
    {
    	public static void Main()
    	{
    		IList<int> intList = new List<int>(){ 10, 20, 30, 40 };
    
    
    		Console.WriteLine(intList.Count);
    
    		IList<Student> studentList = new List<Student>() { 
                    new Student(){ StudentID=1, StudentName="Bill"},
                    new Student(){ StudentID=2, StudentName="Steve"},
                    new Student(){ StudentID=3, StudentName="Ram"},
                    new Student(){ StudentID=1, StudentName="Moin"}
                };
    		
    		Console.WriteLine(studentList.Count);
    		
    	}
    }
    
    public class Student
    { 
    	public int StudentID { get; set; }
    	public string StudentName { get; set; }
    	
    }
    
**Resultado:**

    4  
    4
**Ejemplo recorrer una colección**

    using System;
    using System.Collections.Generic;
    
    public class Program
    {
    	public static void Main()
    	{		
    		List<int> intList = new List<int>() { 10, 20, 30, 40, 50 };
    
    		intList.ForEach(el => Console.WriteLine(el));
    
    		foreach (var el in intList)
            	Console.WriteLine(el);
    		
    		for(int i =0; i < intList.Count; i++)
    			Console.WriteLine(intList[i]);
    		
    	}
    } 

**Resultado:**

    10  
    20  
    30  
    40  
    50  
    10  
    20  
    30  
    40  
    50  
    10  
    20  
    30  
    40  
    50

**Ejemplo insertar elementos en la colección**

    using System;
    using System.Collections.Generic;
    					
    public class Program
    {
    	public static void Main()
    	{
    		IList<int> intList = new List<int>(){ 10, 20, 30, 40 };
    
    		intList.Insert(1, 11);// inserts 11 at 1st index: after 10.
    		
    		foreach (var el in intList)
    			Console.WriteLine(el);
    	}
    }


Resumen

Desafio




> Fuentes
[https://medium.com/@richmoore_35579/net-c-collections-programming-b35aa29653a7](https://medium.com/@richmoore_35579/net-c-collections-programming-b35aa29653a7)
[https://www.tutorialsteacher.com/csharp/csharp-list](https://www.tutorialsteacher.com/csharp/csharp-list)
[https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/collections](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/collections)
[https://docs.microsoft.com/es-es/dotnet/csharp/tutorials/intro-to-csharp/arrays-and-collections](https://docs.microsoft.com/es-es/dotnet/csharp/tutorials/intro-to-csharp/arrays-and-collections)
[https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/concepts/collections#BKMK_KindsOfCollections](https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/concepts/collections#BKMK_KindsOfCollections)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMzQyMTY3OTYsLTQxNzk5MzU3LDU1ND
k4NDI1Nyw4Mjc4Njc3NDMsMTUzMjcxOTE4MCw2NTQzMDIxNDgs
MTQyNDY5MTQ2LDE0NzM2NDA5NTksLTU3MDY2MDY2NCw4MjY2OT
EzMjgsMTQ0MTg3NjUyLDU2ODU5NDc1OCwtNDg1NzY3NTMxLC03
Mzg3MDQ1NTVdfQ==
-->