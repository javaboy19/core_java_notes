### What is wrapper class?
A Wrapper class is a class whose object wraps or contains a primitive data types. When we create an object to a wrapper class, 
 it contains a field and in this field, we can store a primitive data types. In other words, we can wrap a primitive value 
 into a wrapper class object.
 
 ### Why we need wrapper class?
 1. Wrapper class convert primitive data type to objects.
 2. Data structure in collections framework,such as Vector, ArrayList stores  only objects(reference types),in this case wrapper classes 
 can help.
 3. The classes in java.util handles only objects hence in this case wrapper class can help.
 4. Objects are very useful and need in synchronization and multithrading.
 
                    Primitive data types and their corresponding wrapper classes
  | Premitive types    | Wrapper classes          |
| ------------- |:-------------:
| int     | Integer | 
| char    | Character      |   
| byte | Byte    |   
|short|Short|
|long|Integer|
float|Float|
double|Double
boolean|Boolean
---
Java program to demonstrate Wrapping and UnWrapping  in Java Classes 
---
          class WrappingUnwrapping 
          { 
            public static void main(String args[]) 
              { 
                 //  byte data type 
                  byte a = 1; 

                 // wrapping around Byte object 
                  Byte byteobj = new Byte(a); 

               // int data type 
               int b = 10; 

              //wrapping around Integer object 
              Integer intobj = new Integer(b); 

              // float data type 
              float c = 18.6f; 

              // wrapping around Float object 
              Float floatobj = new Float(c); 

              // double data type 
              double d = 250.5; 

              // Wrapping around Double object 
              Double doubleobj = new Double(d); 

              // char data type 
              char e='a'; 

              // wrapping around Character object 
              Character charobj=e; 
  
              //  printing the values from objects 
              System.out.println("Values of Wrapper objects (printing as objects)"); 
              System.out.println("Byte object byteobj:  " + byteobj); 
              System.out.println("Integer object intobj:  " + intobj); 
              System.out.println("Float object floatobj:  " + floatobj); 
              System.out.println("Double object doubleobj:  " + doubleobj); 
              System.out.println("Character object charobj:  " + charobj); 
  
              // objects to data types (retrieving data types from objects) 
              // unwrapping objects to primitive data types 
              byte bv = byteobj; 
              int iv = intobj; 
              float fv = floatobj; 
              double dv = doubleobj; 
              char cv = charobj; 
  
              // printing the values from data types 
              System.out.println("Unwrapped values (printing as data types)"); 
              System.out.println("byte value, bv: " + bv); 
              System.out.println("int value, iv: " + iv); 
              System.out.println("float value, fv: " + fv); 
              System.out.println("double value, dv: " + dv); 
              System.out.println("char value, cv: " + cv); 
              } 
          } 
Output:          
---
              Values of Wrapper objects (printing as objects)
              Byte object byteobj:  1
              Integer object intobj:  10
              Float object floatobj:  18.6
              Double object doubleobj:  250.5
              Character object charobj: a
              Unwrapped values (printing as data types)
              byte value, bv: 1
              int value, iv: 10
              float value, fv: 18.6
              double value, dv: 250.5
              char value, cv: a

Autoboxing and Unboxing
---
Autoboxing: Automatic conversion of primitive types to the object of their corresponding wrapper classes is known as autoboxing. 
For example – conversion of int to Integer, long to Long, double to Double etc.

                // Java program to demonstrate Autoboxing 

                import java.util.ArrayList; 
                class Autoboxing 
                { 
                  public static void main(String[] args) 
                  { 
                    char ch = 'a'; 

                    // Autoboxing- primitive to Character object conversion 
                    Character a = ch; 

                    ArrayList<Integer> arrayList = new ArrayList<Integer>(); 

                    // Autoboxing because ArrayList stores only objects 
                    arrayList.add(25); 

                    // printing the values from object 
                    System.out.println(arrayList.get(0)); 
                  } 
                } 
                
  Output:
          25
          
          
Unboxing: It is just the reverse process of autoboxing. Automatically converting an object of a wrapper class to its corresponding primitive type is known as unboxing. 
For example – conversion of Integer to int, Long to long, Double to double etc.


              // Java program to demonstrate Unboxing 
              import java.util.ArrayList; 

              class Unboxing 
              { 
                  public static void main(String[] args) 
                  { 
                      Character ch = 'a'; 

                      // unboxing - Character object to primitive conversion 
                      char a = ch; 

                      ArrayList<Integer> arrayList = new ArrayList<Integer>(); 
                      arrayList.add(24); 

                      // unboxing because get method returns an Integer object 
                      int num = arrayList.get(0); 

                      // printing the values from primitive data types 
                      System.out.println(num); 
                  } 
              } 

Output:

        24
Comparison of Autoboxed Integer objects in Java
---
When we assign an integer value to an Integer object, the value is autoboxed into an Integer object. For example the statement “Integer x = 10” creates an object ‘x’ with value 10.

Following are some interesting output questions based on comparison of Autoboxed Integer objects.

Predict the output of following Java Program:

              // file name: Main.java 
              public class Main { 
                public static void main(String args[]) { 
                  Integer x = 400, y = 400; 
                  if (x == y) 
                    System.out.println("Same"); 
                  else
                    System.out.println("Not Same"); 
                } 
              } 
Output:
          Not Same   
        
              The output of following program is a surprise from Java. 
              // file name: Main.java 
              public class Main { 
                public static void main(String args[]) { 
                  Integer x = 40, y = 40; 
                  if (x == y) 
                    System.out.println("Same"); 
                  else
                    System.out.println("Not Same"); 
                } 
              } 
Output:

        Same

In Java, values from -128 to 127 are cached, so the same objects are returned. 
The implementation of valueOf() uses cached objects if the value is between -128 to 127.

If we explicitly create Integer objects using new operator, we get the output as “Not Same”. 
See the following Java program. In the following program, valueOf() is not used.

          // file name: Main.java 
          public class Main { 
            public static void main(String args[]) { 
              Integer x = new Integer(40), y = new Integer(40); 
              if (x == y) 
                System.out.println("Same"); 
              else
                System.out.println("Not Same"); 
            } 
          } 

Output:

        Not Same

Predict the output of the following program:

            class GFG 
            { 
              public static void main(String[] args) 
              { 
              Integer X = new Integer(10); 
              Integer Y = 10; 

              // Due to auto-boxing, a new Wrapper object 
              // is created which is pointed by Y 
              System.out.println(X == Y); 
              } 
            } 
Output:

      false

Explanation: Two objects will be created here. 
First object which is pointed by X due to calling of new operator and second object will be created because of Auto-boxing.

Reference blog link: https://www.geeksforgeeks.org/comparison-autoboxed-integer-objects-java/
                     https://www.geeksforgeeks.org/wrapper-classes-java/
