# HotelReservation microservices and distributed cloud Blueprint
There are a plenty of examples of different of microservices that utilize .Net Core as platform as domain designs. The one comes to mind is documented quite well by Microsoft EShopContainers Microfrontend blueprints.
Here’s a revised version of the text with improved structure and flow:

---

There are numerous examples of microservices utilizing .NET Core as a platform for implementing domain-driven designs. A well-documented example is Microsoft's **eShopOnContainers**, which provides detailed blueprints for microservices and microfrontends.  

In contrast, Python has fewer comprehensive examples of microservices that demonstrate business domain applications. While there are several GitHub repositories showcasing FastAPI as a library for microservices, detailed domain-specific examples are scarce. One notable exception is the book *Architecture Patterns with Python* by Harry Percival and Bob Gregory. This book effectively demonstrates the use of Flask API in creating microservices and microfrontends, offering valuable insights into architecture patterns.  

Drawing inspiration from this manuscript, a fictional **Hotel Reservation** microservices application was developed, utilizing FastAPI within **Azure Kubernetes Service (AKS)** and **Amazon Elastic Kubernetes Service (EKS)**. This system employs the **CQRS (Command Query Responsibility Segregation)** pattern. However, an unexplored area in Python implementations is the integration of the **Middleware Pattern**, **Event Sourcing**, and the **Circuit Breaker Pattern** for peer-to-peer distributed communication.  

The conventional approach for messaging queues in microservices often relies on systems like Kafka or Redpanda for publisher-subscriber patterns. However, these systems can become single points of failure. In response to these limitations, cloud standards groups (including those this author has contributed to) have favored **Azure Event Bus** or **Event Hub** over Kafka, primarily to avoid the complexity of maintaining ZooKeeper.  

This repository explores ideas based on the **Saga choreography pattern** for managing distributed transactions, paired with peer-to-peer microservices. The design incorporates archival of event stores in cloud-based blob storage providers or structured databases like PostgreSQL. Several of these concepts draw upon the **Backend for Frontend (BFF)** pattern, previously employed in the author's work.  

The BFF API gateway pattern simplifies the communication between UI frontends and backend APIs. It enables a modern pipeline for executing various HTTP commands and queries, enhancing scalability when deployed to Azure AKS or other containerized ecosystems.  

This exploration aims to provide a practical and modern approach to microservices architecture while addressing limitations in existing Python implementations.  

**References:**  
- [Saga Pattern Overview](https://microservices.io/patterns/data/saga.html)  
- [Eventuate Tram Core Repository](https://github.com/eventuate-tram/eventuate-tram-core)

--- 

This revised version improves readability, structure, and coherence while retaining all critical details.

## Scope for the project
*  Develop distributed mico-services for managing hotel reservations, check-ins, upgrades and potential machine learning integration for seasonal predictions.
## The core technololgy covered by blueprint: 
* CQRS (Command Query Responsibility Segregation) for execution of HTTPs requests.
* Event Sourcing and Event Store for both event notification and event publishing.
* Middleware Pattern - for logging, authenticaion with OpenID, request throttoling.
* Circuit Breaker design - for the request retry mechanisms.  
* Saga choreagrphy methodology to enable peer-to-peer event communication between microservices.
 
Python will be primary DSL for this implementation. The FAST Api is a web framerwork for constucting application.  PostgreSQL will be used for event logging in oroder to assure durability of messages.

The services will expose HTTP endpoints to perform CRUD (Create, Read, Update, Delete) operations on hotel reservations, rooms, and customers. These service should handle various business scenarios, such as creating a new reservation, checking room availability, updating reservation details, and deleting a reservation. The service should also manage hotel room details and customer information efficiently.  The Saga 

