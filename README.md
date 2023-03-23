# Messag_Queue_Section
Message Queue section includes two broker systems in marketing: Kafka and RabbitMQ. And use spring boot to build a microservice architecture to implement asynchronous communication between services. <br>

This section consists of five directories, and with detailed comments and documentation. The general introduction on message queue could refer to my [medium blog](https://medium.com/@sudacgb/message-queue-a-complete-guide-aa956ada2e98) . <br>

**Spring-Kafka-Tutorial**<br>
And this application just run on local machine, causing producer, broker, consumer are on the same machine. That is why in the application.properties file, we configure producer port, consumer port all 9092. And we also need to configure serializer and desserializer for kafka. <br>
In KafkaTopicConfig, we create topic by using TopicBuilder() and these beans will be managed by ApplicationContext container. <br>
Build producer and consumer in kafka folder, and we send message by using kafkatemplate provided by kafka library, but we need to encapsulate our message(String, or JSON) in to Message object also configure topic name then send(Message) to MQ. <br>
Consumer service should use Listener annotation to configure topic name to get message from MQ. <br>


**Spring-Kafka-real-word-project**<br>
This project just utilizes the property of streaming data processing of Kafka. And consumer side is continuously pull updated information from Wikimedia webpage and put them into Kafka message queue. And consumer subscribe to this topic and continuously pull message out and store these message into RDMS-MySQL. <br>
Producer side just configure the key-value serializer and topic name. Application extends **CommandLineRunner** interface to override run() method, and this method will be extected when the application start. <br>
Consumer side just configure key-value deserializer and Datasource information. And user Listener annotation to listen to specific topic. <br>

