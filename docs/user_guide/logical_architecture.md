# logical architecture

Defining the logical architecture of an application consists in combining services to meet the internal and external needs of the application.

The external services represents ways for the application to communicate with outside world: receive traffic or send outgoing requests, messages... In other words, it defines an external contract for the application.

The internal services represents building blocks an application use to fullfill it external contract: compute capabilities, storage... 

The available services are:

* external services
    * [web gui service](web_gui_service.md) - provides inbound network connectivity for exposing UIs
    * ~~SOAP/REST web service consummer~~
    * ~~SOAP/REST web service provider~~
    * ~~asynchronous middleware service (JMS)~~
* internal services
    * processing related services
        * ~~JEE processing service (Jonas-based JEE support)~~
        * [Cf-Java processing](cf_java_processing_service.md): The Java processing service is an internal service that provides the ability to run java component inside an application server container.
    * data related services
        * [relational database service](relational_database_service.md) - El PaaSo relational database service (RDS) provides you relational databases like MySQL or PostgreSQL.
        * ~~blob store service~~
    * communication related services
        * ~~internal MOM service - The Internal MOM Service provides the ability to send and receive asynchronous messages that are consumed within the same application using the JMS API.~~
        * [internal RabbitMQ service](internal_rabbitmq_service.md) - The Internal RabbitMQ Service provides the ability to send and receive asynchronous messages that are consumed within the same application using RabbitMQ message broker.
    * management related services
        * [configuration service](configuration_service.md) - Formalizes the supported configuration entries that the app exposes

![a sample logical architecture](sample_logical_architecture.png)
a sample logical architecture