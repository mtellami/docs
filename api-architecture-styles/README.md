<div align="center">

# 🪩 API architecture styles 🪩

<img src="src/api.png" width="100%" />
</div>

An application programming interface is a way for two or more computer programs to communicate with each other. It is a type of software interface, offering a service to other pieces of software.

## 🔷 REST
REST is a way to use web standards and addresses to work with data on a server. They’re popular, easy to implement, and use HTTP methods. Most of the web services you interact with daily, like Twitter or YouTube, are powered by Restful APIs. For example, a client can use GET to get data, POST to make new data, PUT to change data, or DELETE to remove data. The data are usually in formats like JSON or XML.

### 🔸 Pros
- It is simple and easy to use and understand.
- It follows the rules of the web and uses existing standards and protocols.
- It is fast and can handle many requests, as it supports caching and statelessness.
- It is flexible and can use different formats and media types.

### 🔸 Cons
- It does not have a clear contact or schema, which make it unclear and inconsistent.
- It does not support complex queries or operations, which can make it need many requests and get too much or too little data.
- It does not handle errors or exceptions well, as it uses HTTP status codes that are not always clear or correct.

### 🔸 Usage
REST is good for situations where:
- The data model is simple and stable.
- The clients and servers are not dependent on each other.
- The speed and scalability are important.


## 🔷 SOAP
SOAP is s style that uses XML messages and a predefined contract to exchange information between applications. It has a clear and strict contract, and it supports complex queries and operations, but it is complex, verbose, and not scalable or performant.

### 🔸 Pros
- It has a clear and strict contract that ensure interoperability and compatibility.
- It support complex queries and operations, such as transactions, security or authentication.
- It handles errors and exceptions well, as it uses SOAP faults that provide detailed information.

### 🔸 Cons
- It is complex and verbose to use and understand.
- It does not follow the principles of the web and adds overhead to the existing protocols.
- It is not scalable or performant, as it does not support caching or statelessness.
- It is not flexible or extensible, as it requires changes to the contracts for any modification.

### 🔸 Usage
SOAP is suitable for scenarios where:
- The data model is complex and dynamic.
- The clients and servers are tightly coupled and dependent.
- It’s heavily used in financial services and payment gateways where security and reliability are key.


## 🔷 GraphQL
GraphQL is not just an architectural style but also a query language, allowing clients to ask for specific data as they need. This means no more over-fetching or under-fetching of data. You ask for exactly what you need. This leads to more efficient network communication and faster responses. Facebook developed GraphQL to deliver efficient and precise data to its billions of users. Now it’s used by companies like GitHub and Shopify. Its flexibility and efficiency make it a strong choice for applications with complex data requirements. It also supports mutations to change the data, and subscriptions to get live updates when the data changes.

### 🔸 Pros
- It works with any server language or framework, as it uses its own schema definition language.
- It has a single endpoint, which makes it more efficient than REST, where multiple requests might be needed to get enough data.
- It is strongly typed, which makes sure the data is consistent and compatible between the client and the server.
- It lets clients fetch only the data they need, which avoids over-fetching or under-fetching of data.

### 🔸 Cons
- It is complex and hard to use and understand, as it requires learning a new syntax and logic.
- It does not support caching by default, which can affect performance and scalability.
- It does not handle errors well, as it always returns HTTP 200 status code, even if there are errors in the GraphQL layer.

### 🔸 Usage
GraphQL is good for situation where:
- The data model is complex and dynamic, as it can handle nested and relational data.
- The clients and servers are not dependent on each other, as it lets clients define their own data requirements.
- The bandwidth and performance are important, as it reduces the amount of data transferred.


## 🔷 gRPC
gRPC is modern, high-performance, and uses protocol buffers. It’s a favorite for microservices architectures, and companies like Netflix use gRPC to handle their immense interservice communication. However, if you’re dealing with browser clients, gRPC might pose some challenges due to limited browser support.

### 🔸 Pros
- It has a clear and strict contract, which ensures interoperability and compatibility between services.
- It supports complex queries and operations, such as streaming, bidirectional communication, authentication, or encryption.
- It is fast and efficient, as it uses binary format and HTTP/2 features to reduce latency and bandwidth.

### 🔸 Cons
- It is complex and hard to use and understand, as it requires generating and compiling protocol buffer files.
- It does not follow the principles of the web, as it uses custom headers and methods that are not compatible with standard web tools or browsers.

### 🔸 Usage
gRPC is good for situation where:
- The data model is complex and dynamic, as it can handle structured and unstructured data.
- The services are dependent on each other, as it allows services to invoke each other’s methods directly.
- The speed and efficiency are important, as it minimizes the overhead and maximizes the throughput.


## 🔷 WebSockets
WebSocket is all about real-time, bidirectional, and persistent connections. It’s perfect for live chat applications and real-time gaming, where low-latency data exchange is crucial.

### 🔸 Pros
- It is faster and more efficient than HTTP, as it uses a single connection and does not need headers or cookies for each message.
- It can send and receive different types of messages over the same connection, such as text, binary, or streaming data.
- It can push data from the server to the client without waiting for a request, which enables real-time and event-driven communication.

### 🔸 Cons
- It’s not supported by some older browsers or proxies that do not understand the WebSocket protocol or the upgrade header.
- It’s not secure by default, as they do not use encryption or authentication unless they use the wss:// scheme, which is similar to https:// for HTTP.
- It does not store any information about the connection or the messages on either side, which means they are not stateful.

### 🔸 Usage
WebSocket is good for situations where the web application needs:
- Fast and interactive data exchange, such as chat, gaming, or streaming.
- Bidirectional and multiplexed communication, where both sides can send and receive multiple messages of different types at the same time.
- Real-time and event-driven communication, where the server can send data to the client without waiting for a request.

## 🔷 Webhooks
Webhooks are a way for servers to send messages to clients when something happens. They use HTTP callbacks or POST requests to deliver payloads that contain information about the events. The clients register their webhooks with the servers by providing URLs that can receive the payloads. Webhook is all about event-driven, HTTP callbacks, and asynchronous operation.

### 🔸 Pros
- It is simple and easy to use and understand, as it uses standard HTTP methods and formats.
- It follows the principles of the web, as it leverages existing standards and protocols.
- It is scalable and performant, as it supports asynchronous communication without polling or waiting.

### 🔸 Cons
- It does not have a clear or strict contract, which can lead to inconsistency and ambiguity between servers and clients.
- It does not support complex queries or operations, it only sends one-way notifications without confirmation or feedback.
- It does not handle errors well, It does not provide retries or acknowledgments in case of failures.

### 🔸 Usage
Webhooks is good for situations where:
- Event-driven notifications ( GitHub uses webhooks to notify your other systems whenever a new commit is pushed.)
- The data model is simple and stable, as it can handle basic types and fields.
- The servers and clients are not dependent on each other, as they do not require direct communication or coordination.
- The performance and scalability are important, as they reduce the load and latency of the communication.

