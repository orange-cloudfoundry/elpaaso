This user guide will provide you every piece of information that will lead you to El PaaSo.

## programming model

To ensure a fast and reliable service, the paas requires to follow a particular programming model.

* external services
    * [using the web gui service](web_gui_service.md) - The web graphical user interface service (web GUI) is an external service that provides the ability to publish a graphical user interface on http or https protocol.
    * SOAP/REST web service consummer
    * SOAP/REST web service provider
* internal services
    * [processing service](cf_java_processing_service.md) - The Java processing service is an internal service that provides the ability to run java component inside an application server container.
    * [configuration service](configuration_service.md)
    * [relational database service](relational_database_service.md) - El PaaSo relational database service (RDS) provides you relational databases like MySQL or PostgreSQL.
    * blob store service
    * internal MOM service - The Internal MOM Service provides the ability to send and receive asynchronous messages that are consumed within the same application using the JMS API.
    * [internal RabbitMQ service](internal_rabbitmq_service.md) - The Internal RabbitMQ Service provides the ability to send and receive asynchronous messages that are consumed within the same application using RabbitMQ message broker.

## using El PaaSo

The Elpaaso UI is the main way for users to interact with the PaaS.
An [SOAP API](north_api.md) is also available.

Additionally you can start [using the sample applications available in the PaaS](sample_applications.md).