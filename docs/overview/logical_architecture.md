# logical architecture

Defining the logical architecture of an application consists in combining services to meet the internal and external needs of the application.

The external services represents ways for the application to communicate with outside world: receive traffic or send outgoing requests, messages... In other words, it defines an external contract for the application.

The internal services represents building blocks an application use to fullfill it external contract: compute capabilities, storage... 

The available services are:

* processing related services
    * ~~JEE processing service (Jonas-based JEE support)~~
    * Cf-Java processing: java-buildpack support 
    * graphical user interface (GUI) service (web interface)
* data related services
    * non-relational data storage service (Store as a Service, like Amazon Simple Storage Service, Amazon S3)
    * relational database service (Database as a Service)
* communication related services
    * asynchronous middleware service (MOM as a Service, JMS)
    * synchronous webservice (SOAP/REST APIs as a Service)
* management related services
    * consolidated logs query tool service (Log as a Service)
    * application monitoring service (Monitoring as a Service)
    * application configuration service (Configuration as a Service)

![a sample logical architecture](sample_logical_architecture.png)
a sample logical architecture