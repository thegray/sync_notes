---

Tags : #rabbitmq #research #notes
Back Links :
Date : {{27-04-2022}} 22:13

---

# rabbitmq notes
## Using Exchange
### type: direct
- message will flowing to consumer with same *routing key*
- to achieve *round-robin* message dispatching, each consumer that connect to the exchange should declare same queue. this is because rabbit will bind random named queue to the exchange if not supplied with queue name.


## Message Publishing Features
### Mandatory
- If set to true, server will return the message to publisher if server failed to route the message to at least one queue.

### Persistent
- Messages marked as 'persistent' that are delivered to 'durable' queues will be logged to disk. Durable queues are recovered in the event of a crash, along with any persistent messages they stored prior to the crash.

