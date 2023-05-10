# full-cycle-2.0-rabbitmq

Files I produced during the RabbitMQ classes of my [Microservices Full Cycle 3.0 course](https://drive.google.com/file/d/1bJnFxQPKgSsI30sCvW-KzYK4V5JWzgSs/view?usp=share_link).

## RabbitMQ connections architecture

In RabbitMQ, you can use the same TCP connection to receive and send messages. To do that, you just need to use two different channels inside the same TCP connection.

![Only one persistent connection between client and server doing multiplexing](./rabbitmq-tcp-connection-multiplexing.png)

## Examples using [RabbitMQ Simulator](http://tryrabbitmq.com/)

### 1 Producer, 1 Exchange, 1 Queue and 1 Consumer

![Message sending animation](./1producer-1exchange-1queue-1consumer.gif)

### 1 Producer, 1 Exchange, 1 Queue and 2 Consumers

As both consumers are subscribed to the same queue, when one consumer get a message, the message is removed from the queue and the other consumer needs to wait for a new message to get it.

![Message sending animation](./1producer-1exchange-1queue-2consumer.gif)

### 1 Producer, 1 Exchange, 2 Queues and 3 Consumers

Note that when I create the new queue and connect it to the exchange setting the routing key as y, when I change the producer routing key to y, the messages only go to the queue y.

![Message sending animation](./1producer-1exchange-2queue-3consumer.gif)

### 1 Producer, 1 Exchange in fanout mode, 3 Queues and 4 Consumers

Note that the exchange in fanout mode sends the messages to all queues connected to them. Also, as I created a queue without anyone consuming it's messages, it started to accumulate the messages and as soon as I created the consumer for it, the queue started to be emptied.

![Message sending animation](./1producer-1_fanout_exchange-3queue-4consumer.gif)

### 1 Producer, 1 Exchange in topic mode, 3 Queues and 4 Consumers

Note that the exchange in topic mode sends the messages to all connections that match a pattern.

![Message sending animation](./1producer-1_topic_exchange-3queue-4consumer.gif)
