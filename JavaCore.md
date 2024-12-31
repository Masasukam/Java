# Core Java

### Overview Dec 17, Tuesday 
![image](https://github.com/user-attachments/assets/0f6b5205-fe9c-4093-a72c-4036ca4322ed)

- Hierarchy
  - User sends requests to server from their device(frontend), and getting responses from relevant microservices through API gateway
  - Microservices, each is a server (small) to handle a specific module/logic/functionality.
    - Can have multiple servers working with the same functionality (10 servers for user management, in case there are billions of users)
    - Each microservice has its own database (can have multiple databases within the same microservice)
    - data can flow/communicate between microservices
    - Each microservice can be implemented by different language & framework
  - Cache: Connected with frontend, can be anywhere in the backend, or in the middle between frontend-backend. To reduce time retrieving data from database
    (too costly to tralvel all the way to database each time)
  - Other servers:
    - Config servers: manages all the configuration of all the microservices
    - Service and Registry and Discovery
    - Elalstic Search (ELK)
- API Gateway: Intersects all requests
  - authentication
  - There are monitor, logs in the backend
- Databases
  - Can have multiple in the backend, can be different types (both relational or non-relational)
- Communication
  - data can flow/communicate between microservices
  - sync: waiting at the counter until the coffee is made
  - async (message queue): do something else while the coffee is being made, come back when ready
    - requesting microservice sends a message to the queue, responsing microservice receives the message from the queue and process the message when available
   
### Strings, Data Structures - Dec 18, Wednesday
- String
  - ![image](https://github.com/user-attachments/assets/eaf16312-7bb2-44a2-8891-45aaad814cdb)

  - String vs stringbuilder vs stringBuffer
  - String object and pool
  - Integer object and pool: put in the pool if < 128
  - == compares object/address, not value
  - .equals needs to be overwritten (with hashcode), otherwise same as ==
- Data Structures
  - ![image](https://github.com/user-attachments/assets/d9f48e55-bd24-4818-819f-d5ccbbee622b)

  - Collection vs Collections
  - Collection: Set, List, Queue
    - Set: HashSet, LinkedHashSet, TreeSet
    - List: LinkedList vs ArrayList
    - Queue: PriorityQueue -> heap
  - Map: HashMap, LinkedHashMap, HashTable, CurrentHashMap, TreeMap
 
### JVM, KeyWords, OOP, Exceptions - Dec 19, Thursday
Compiled vs. interpreted
- Translate all code at once, interpreted translates line by line


**JVM** - https://www.freecodecamp.org/news/jvm-tutorial-java-virtual-machine-architecture-explained-for-beginners/
- ![image](https://github.com/user-attachments/assets/71bbd982-a0b1-4bf1-a34c-8025e75b272e)

- Class Loader: bootstrap / extension/ application class extension
- Runtime Data Area
  - method area: static, pool
  - Heap Area: objects initialized using "new" keyword
  - Stack Area: multi threads
  - PC register area: multi threads
  - native method stack
- Execution Engine
  - interpreter: executing byte code after compileling .java file to .class (byte code)
  - JIT compiler
  - Garbage Collector
    - Serial
    - Parallel
    - G1: scan each chunk and does GC based on priority
   

**KeyWords**
- modifiers
  - public/private, protected, static, final, abstract, synchronized, native, strictfp, transient, volatile
    - final variable needs to be initialized, pointer can't be updated.
      - Can use another pointer to point to the object, then modify object's value
    - final method can't be overriden
    - final class can't be inherited
    - static is global, shared among all instances
      - can be static variable, method, class (can't be at top level), block
        
**OOP**
- Inheritance
  - implements: can implement multiple interfaces
  - extends: only able to extend one interface / class
- Encapsulation
  - data protection
  - private, and use getter and setter
- Abstraction: abstract class, interface (by extend and implements)
- Polymorphism:
  - overload: compile time
  - override: runtime
    
**Exceptions**
- checked (compile time): IO
  - need to be handled by try-catch-finally
  - can do try-finally combo and try-catch combo
- unchecked (runtime): NULL pointer

### Generics, Java Features - Dec 20 Friday
**Generics**
- generic class allows you to create a single class definition that works with different data types, enhancing code reusability and type safety. You define a generic class using a type parameter (T, E, K, V, etc.) that can be replaced with actual types when creating an instance of the class.
  - ```
    // Define a generic class
    public class Box<T> {
        private T item;
    
        public void setItem(T item) 
            this.item = item;
  
        public T getItem()
            return item;
    }
    
    public class Main {
        public static void main(String[] args) {
            // Create a Box instance for Integer
            Box<Integer> integerBox = new Box<>();
            integerBox.setItem(123);
            System.out.println("Integer Box: " + integerBox.getItem());
    
            // Create a Box instance for String
            Box<String> stringBox = new Box<>();
            stringBox.setItem("Hello Generics");
            System.out.println("String Box: " + stringBox.getItem());
        }
    }
    ```
- A generic method is a method that can operate on different types. You define a generic method by including the type parameter before the method's return type.
  - ```
    public class Utility {
        // Generic method
        public static <T> void printArray(T[] array) {
            for (T element : array)
                System.out.print(element + " ");
            System.out.println();
        }
    }
    
    public class Main {
        public static void main(String[] args) {
            Integer[] intArray = {1, 2, 3, 4, 5};
            String[] strArray = {"A", "B", "C"};
    
            Utility.printArray(intArray);
            Utility.printArray(strArray);
        }
    }
    ```

**Java Features**
- Lambda expressions: It simplifies the code and improves reading, no need to create object instance.
  - syntax :  (arguments)  → {body}
  - ![image](https://github.com/user-attachments/assets/07152e0d-5718-49d7-b82e-a4c869def7e0)
- Functional Interface (works together with lambda)
  - A functional interface in Java is an interface with exactly one abstract method. It can contain default and static methods but only one abstract method.
  - ```
    @FunctionalInterface
    interface MathOperation {
        int operate(int a, int b); // Single abstract method
    }
  
    public static void main(String[] args) {
        MathOperation addition = (a, b) -> a + b;
        System.out.println("Result: " + addition.operate(5, 3)); // Output: 8
    }
    ```
- Default method: It is a method that is defined in a interface, can be overriden by sub classes
- Optional Class is a container object which may or may not contain a non-null value. Instead of returning a null value, methods return an Optional object, allowing the caller to explicitly check if a value is present or not.
  - ![image](https://github.com/user-attachments/assets/8256f350-07cd-47fa-90c6-7517e9825a5a)
- Stream
  - ![image](https://github.com/user-attachments/assets/07a6a673-1b16-420b-bf46-1bf3f89fa441)
  - ![image](https://github.com/user-attachments/assets/6346ee44-f989-49e4-b967-3b07d4760f5a)
  - ![image](https://github.com/user-attachments/assets/130825f8-8a75-427e-b09c-c514ea537aca)

### Thread, Lock - Dec 23 Monday
- Regular threads can only extend the Thread class
- Runnable threads implement the Runnable Interface, can implement multiple interfaces
- Callable threads implements the Callable interface, can return a value and throw checked exceptions.
  - Return Type: T (generic type, returned by the call() method).
  - Execution submitted to an ExecutorService
- ![image](https://github.com/user-attachments/assets/6b5f580d-d439-442b-8e28-d4a59233c705)

**ThreadPool**
- Executors is an utility class (ExecutorService is an interface)
- Basic components includes: Task Queue, Worker Thread, Executor(Pool)
- submit(Callable/Runnable task), return result
- https://www.youtube.com/watch?v=msay7O2NdLw






 


