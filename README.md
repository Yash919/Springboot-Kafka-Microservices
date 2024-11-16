# Springboot-Kafka-Microservices

## Objective

The application simulates an order processing system where the Order Service publishes events to a Kafka topic, and the Stock Service and Email Service consume those events to perform specific operations.

## Architecture Flow
#### Order Service:
- Handles order placement requests from the client.
- Publishes an OrderEvent to a Kafka topic.
#### Stock Service:
- Listens to the Kafka topic.
- Processes the OrderEvent to update stock details in the database.
#### Email Service: (Needs to be implemented)
- Listens to the Kafka topic.
- Sends an email notification to the customer about their order status.

## Technologies Used
- **Spring Boot**: Microservices framework.
- **Apache Kafka**: Event streaming platform.
- **JSON**: For event serialization and deserialization.


## Configuration Details
Each service has its specific Kafka consumer/producer configurations. Below are the key configurations:

#### Common Kafka Configuration
- bootstrap-servers: ```localhost:9092```
- Topic: ```order_topics```
- Order Service
- Endpoint: POST ```/api/v1/orders```
- Payload:
  ``` 
  "orderName": "Sample Order",
  "quantity": 5,
  "price": 100 
  ```
<br><br>
  <img width="1091" alt="image" src="https://github.com/user-attachments/assets/83421c70-dfcc-4817-a185-0e96bce45e17">


#### Stock Service
Consumes ```OrderEvent``` from ```order_topics```.
Updates stock in the database (simulated).

#### Email Service
Consumes ```OrderEvent``` from ```order_topics```.
Sends email notifications (simulated). (Note**  Need to implement)

## Example Workflow
- Place an order via Order Service API.
- Order Service publishes the OrderEvent to Kafka.
- Stock Service consumes the event and logs the stock update.
- Email Service consumes the event and logs the email notification. (need to implement)

## Log Outputs
- Order Service: Logs the published OrderEvent.
- Stock Service: Logs the received OrderEvent and stock update.
- Email Service: Logs the received OrderEvent and email sending simulation.

## Credits
This project was created by Yash Mehta 🚀
