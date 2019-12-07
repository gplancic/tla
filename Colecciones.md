# Colecciones

Para muchas aplicaciones, desea crear y administrar grupos de objetos relacionados. Hay dos formas de agrupar objetos: creando matrices de objetos y creando colecciones de objetos.

Las matrices son muy útiles para crear y trabajar con un número fijo de objetos fuertemente tipados.

Las colecciones proporcionan un método más flexible para trabajar con grupos de objetos.

A diferencia de las matrices, el grupo de objetos con el que trabaja puede aumentar y reducirse dinámicamente a medida que cambian las necesidades de la aplicación.

![List](https://github.com/dev-Niko/tla/blob/master/list.png)

•Una colección es una clase, de modo que antes de poder agregar elementos a una nueva colección, debe declararla. 

•Una colección    genérica cumple la seguridad de tipos para que ningún otro tipo de datos se pueda agregar a ella. 

•Cuando se recupera un elemento de una    colección genérica, no tiene que determinar su tipo de datos ni convertirlo.

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

<!--stackedit_data:
eyJoaXN0b3J5IjpbODI2NjkxMzI4LDE0NDE4NzY1Miw1Njg1OT
Q3NTgsLTQ4NTc2NzUzMSwtNzM4NzA0NTU1XX0=
-->