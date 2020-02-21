# Colecciones en C#

Muchas aplicaciones requieren agrupar objetos por ejemplo una agenda, un   
 catálogo de productos o el mismo sistema de alumnos de la Universidad. 

El número de objetos a agrupar varía por lo que en general tendremos 2 operaciones comunes a realizar  la **adición y eliminación de objetos**. 
 
También sera necesario poder ser capaces de manipular los objetos de este grupo
 - **Búsqueda de objetos**  
 - **Consulta y modificación de objetos**

Hay dos formas de agruparlos: 
 - **Matrices**
 - **Colecciones** 

Las matrices son muy útiles para crear y trabajar con un número fijo de objetos fuertemente tipados.

Las colecciones proporcionan un método más flexible para trabajar con grupos de objetos.

# Tipos de colecciones

.NET Framework proporciona muchas colecciones comunes.  Cada tipo de colección está diseñado para un fin específico.

Colecciones comunes:

**-   Clases System.Collections.Generic**
    
**-   Clases  System.Collections.Concurrent**
    
**-   Clases  System.Collections**

# Colecciones genéricas

Sabemos qué es una colección en términos generales; Es un objeto que contiene un grupo de otros objetos y puede ser trabajado o procesado de alguna manera. Intentemos definir qué queremos decir con genérico.

Lo que esto significa es que podemos diseñar una clase que recibirá parámetros, los tipos de estos parámetros se definen cuando se crea una instancia de un objeto de clase genérico.

Entonces, en el caso de una colección genérica, podemos crear una instancia de una Lista (*list*) que solo contiene cadenas de textos (*strings*). No se pueden agregar elementos de lista que no sean cadenas de textos. Entonces podríamos definir otra Lista que solo acepte números enteros (*integer*), y así sucesivamente. De esta manera, podemos diseñar clases que se puedan reutilizar en muchos contextos diferentes, y aumentar la seguridad de los tipos también.

Es fácil ver por qué los tipos de colección son candidatos ideales para el comportamiento genérico. Una colección es un contenedor, como una bolsa, por ejemplo. 

Entonces, por ejemplo, podríamos crear una clase de colección genérica que nos permita mantener cadenas de texto en un punto de nuestro código, y mantener números enteros en otro punto, en lugar de crear dos clases, una para contener solo cadenas y otra para contener entradas.

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
eyJoaXN0b3J5IjpbLTM3NDExMTE4OCw3NDk0MzY4MiwtNDE3OT
kzNTcsNTU0OTg0MjU3LDgyNzg2Nzc0MywxNTMyNzE5MTgwLDY1
NDMwMjE0OCwxNDI0NjkxNDYsMTQ3MzY0MDk1OSwtNTcwNjYwNj
Y0LDgyNjY5MTMyOCwxNDQxODc2NTIsNTY4NTk0NzU4LC00ODU3
Njc1MzEsLTczODcwNDU1NV19
-->