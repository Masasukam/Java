# Core Java

### Overview Dec 17, Tuesday 

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
   
### Dec 18, Wednesday
- String
  - String vs stringbuilder vs stringBuffer
  - String object and pool
  - Integer object and pool: put in the pool if < 128
  - == compares object/address, not value
  - .equals needs to be overwritten (with hashcode), otherwise same as ==
 
### Dec 19, Thursday
