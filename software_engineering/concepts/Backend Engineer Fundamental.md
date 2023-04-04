## Communication Protocols

### Base

Communications protocols link the frontend to the backend. Understanding how protocols work is a good skill to have for an engineer especially if they want to build a resilient backend application.
Ultimately, learning communication protocols is important for a backend engineer, and it is possible to go as deep as desired in any protocol. Maybe one day you will write an RFC proposing a new protocol.

### Protocols

Almost all the protocols we use and love on the backend are either built on top of TCP or UDP.
TCP is a stream-based connection-oriented protocol while UDP is a message based and connectionless. TCP provides reliable delivery at a cost of connection setup and retransmission. While UDP starts faster but doesn’t have guaranteed delivery.
- HTTP, HTTP2, HTTP3, WebSockets, gRPC


## Web Servers

Web servers deliver static or dynamic content served on top of the HTTP protocol.
Modern web servers support both HTTP/1.1 and HTTP/2. HTTP/3 is slowly getting support as its newer protocol.
CDN is a web server that acts like a cache and communicate with the origin backend web server to get the content. An API gateway is a web server that authenticate user and serve API responses from backend web servers.


## Database Engineering

The idea of a database is simple; Allow multiple users to store and retreive data consistently and in a durable fashion.
That is why understanding the four properties of [ACID](https://database.husseinnasser.com/): atomicity, consistency, isolation, and durability is fundamental to database engineering.
No database system is complete without indexes and at their core B+Trees is tje data structure of choice. How data is organized in tables, documents or graphs all end up as file system pages at the end of the day. Understanding how to get most of your disk I/O read is the core of database engineering.


## Message Formats

Message formats go hand in hand with communication protocols; They describe in-wire format of the message being sent. They usually broken down into two types human readable and non-human readable. Examples are XML, JSON and [protocol buffers](https://youtu.be/46O73On0gyI).
When a client *sends a message* to a backend, it needs to *serialize the message* from the language data structure to the on-wire message format. When the backend *receives the message* it needs to then *deserialize the message* from this format to the language data structure.

## Security

Security is an important topic in the field of software engineering. There are many aspects to security. As a software engineer, it is important to be familiar with the different types of security risks and how to mitigate them.

## Messaging Systems

Messaging systems are becoming increasingly important as we move towards interconnected systems and services. As services start to communicate to each other, coupling and dependencies increase which increases the complexity of building scalable backend applications. Messaging systems are designed to remove this coupling.
Messaging systems at their core support a feature called publish-subscribe where a client can publish a message and other clients can subscribe to consume this content. The choice of architecting how publishing and consumption is made is up to the messaging system. For example, [Kafka](https://youtu.be/R873BlNVUB4) use long-polling model while [RabbitMQ](https://youtu.be/Cie5v59mrTg) uses push model, both has pros and cons.

## Proxies

Proxies are becoming increasingly popular in the engineering world, especially with the introduction of micro-services. The main purpose of a proxy is it receives requests from a client and forward the requests to backend servers. The proxy hides the network layer identity of the original client from the destination server.

You might have heard the forward proxy and reverse proxy used interchangeably. Both the forward proxy and the reverse proxy, receive requests from clients and forward the request to a backend. In the forward proxy, the client explicitly asks for a particular backend server and the proxy fulfills this request. Forward proxies must be configured in the client network proxy section for them to work. In the reverse proxy the client doesn’t know the final backend server, to the client the final destination is the reverse proxy. The client doesn’t know there are more servers on the backend.
A common uses cases of proxies are caching, API gateways, authentication, load balancing and much more. For example a content delivery network (CDN) is a reverse proxy that sends request to the origin backends. Fiddler or MITM are proxies configured on the client side and all requests* get sent to them first. Service meshes are essentially a proxy and a reverse proxy.

## Conclusion

In conclusion, as a backend engineer, it is important to explore different technologies to find what interests you and where your strengths are. Don’t be afraid to experiment and build something cool, even if it’s with a language that may be considered unconventional.

As you gain more experience and expertise, focus on deepening your knowledge in a specific area to become known for your skill in that field. Ultimately, it is important to follow your interests to succeed in the rapidly-evolving world of software engineering.

Always remember, nothing is written in stone, you can change anything. There is no right and wrong way to design or build applications, it all depends on what you are trying to do. You may run into a situation where the technologies we have today work for you. But you might also reach a dead end and might need to invent something that has never been invented before.