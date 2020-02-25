# Colecciones en C#

Muchas aplicaciones requieren agrupar objetos por ejemplo una agenda, un catálogo de productos o el mismo sistema de alumnos de la Universidad. 

El número de objetos a agrupar varía por lo que en general tendremos 2 operaciones comunes a realizar  la **adición y eliminación de objetos**. 
 
También será necesario poder ser capaces de manipular los objetos de este grupo **Búsqueda de objetos**  , **Consulta y modificación de objetos**

Hasta el momento vimos que es posible agrupar objetos en  **Matrices**. Las matrices son muy útiles para crear y trabajar con un número fijo de objetos fuertemente tipados.

En este apartado veremos como trabajar con **Colecciones**, las colecciones proporcionan un método más flexible para trabajar con grupos de objetos.


# Colecciones 

Una colección es un objeto que contiene un grupo de otros objetos y puede ser trabajado o procesado de alguna manera. Por ejemplo una agenda.

.NET Framework ofrece la posibilidad de trabajar con diferentes tipos de colecciones, vamos a implementar a trabajar en este apartado con las que serán de mayor utilidad para resolver futuros ejercicios: **Colecciones Genericas.**

Genérico significa que podemos diseñar una clase que recibirá parámetros, los tipos de estos parámetros se definen cuando se crea una instancia de un objeto de clase genérico.
Especificamente trabajaremos con las colecciones genericas del tipo List<t>
Instanciación de una colección genérica del tipo List<T> (**T** = Tipo de elementos de la lista.):

    List<int> intList = new List<int>();
    
Entonces, en el caso de una colección genérica, podemos crear una instancia de una Lista (*list*) que solo contiene cadenas de textos (*strings*). No se pueden agregar elementos de lista que no sean cadenas de textos. Entonces podríamos definir otra Lista que solo acepte números enteros (*integer*), y así sucesivamente. De esta manera, podemos diseñar clases que se puedan reutilizar en muchos contextos diferentes, y aumentar la seguridad de los tipos también.

El punto más importante es que al implementar una colección, se proporcionan algunos métodos y propiedades estándar como agregar, editar, recorrer y eliminar, entre otras,  que hacen que el manejo de colecciones sea muy intuitivo.

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
	    	// instancio una lista que solo podrá contener números enteros
    		IList<int> intList = new List<int>();
    		
    		// agrego a la lista 4 números enteros 10,20,30,40
    		intList.Add(10);
    		intList.Add(20);
    		intList.Add(30);
    		intList.Add(40);
    		
    		// imprimo en consola el número de elementos que contiene la lista
    		Console.WriteLine(intList.Count);
    		
	    	// instancio una lista que solo podrá contener cadena de textos
    		IList<string> strList = new List<string>();
    		
    		// agrego a la lista textos, observese que agrego 2 veces "cuatro" y 2 veces null
    		strList.Add("uno");
    		strList.Add("dos");
    		strList.Add("tres");
    		strList.Add("cuatro");
    		strList.Add("cuatro");
    		strList.Add(null);
    		strList.Add(null);
    		
    		// imprimo en consola el número de elementos que contiene la lista
    		Console.WriteLine(strList.Count);
    		
    	    // instancio una lista que contiene objetos del tipo "alumno"
    		IList<Alumnos> alumnoList = new List<Alumno>();
    		alumnoList.Add(new Alumno());
    		alumnoList.Add(new Alumno());
    		alumnoList.Add(new Alumno());
    		
    		Console.WriteLine(alumnoList.Count);
    		
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

> Fuentes
 - [https://medium.com/@richmoore_35579/net-c-collections-programming-b35aa29653a7](https://medium.com/@richmoore_35579/net-c-collections-programming-b35aa29653a7)
 - [https://www.tutorialsteacher.com/csharp/csharp-list](https://www.tutorialsteacher.com/csharp/csharp-list)
 - [https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/collections](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/collections)
 - [https://docs.microsoft.com/es-es/dotnet/csharp/tutorials/intro-to-csharp/arrays-and-collections](https://docs.microsoft.com/es-es/dotnet/csharp/tutorials/intro-to-csharp/arrays-and-collections)
 - [https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/concepts/collections#BKMK_KindsOfCollections](https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/concepts/collections#BKMK_KindsOfCollections)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1NTYwMTA3NjIsMTUxNTQ1NjA2MSwtMT
MxMDY4MDQ0MCwtNTg0Mzg0NjczLDc0OTQzNjgyLC00MTc5OTM1
Nyw1NTQ5ODQyNTcsODI3ODY3NzQzLDE1MzI3MTkxODAsNjU0Mz
AyMTQ4LDE0MjQ2OTE0NiwxNDczNjQwOTU5LC01NzA2NjA2NjQs
ODI2NjkxMzI4LDE0NDE4NzY1Miw1Njg1OTQ3NTgsLTQ4NTc2Nz
UzMSwtNzM4NzA0NTU1XX0=
-->