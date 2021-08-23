# full-cycle-2.0-rabbitmq

Files I produced during the RabbitMQ classes of my [Microservices Full Cycle 2.0 course](https://drive.google.com/file/d/1MdN-qK_8Pfg6YI3TSfSa5_2-FHmqGxEP/view?usp=sharing).

## RabbitMQ connections architecture

In RabbitMQ, you can use the same TCP connection to receive and send messages. To do that, you just need to use two different channels inside the same TCP connection.

![Only one persistent connection between client and server doing multiplexing](./rabbitmq-tcp-connection-multiplexing.png)

