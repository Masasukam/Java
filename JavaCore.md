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
   
### Dec 18, Wednesday - Strings, Data Structures
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
 
### Dec 19, Thursday - JVM
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
