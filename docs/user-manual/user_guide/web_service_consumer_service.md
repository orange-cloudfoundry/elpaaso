## overview

The Web Service Consumer user interface service (web GUI) is an external service that provides the ability to consume a SOAP service provided by other applications.

## usage

The Web Service Consumer allows to define an access point to consume a remote SOAP web service. The external service are brokered by the SOAP Broker. The El PaaSo interface requires few parameters.

## detailed specifications

### user interface attributes

Functional attributes:

* **label**: A label to identify the service on the Web UI. 
* **jndiPrefix**: JNDI prefix chosen for JNDI field lookup. 
* **WS Domain**: WS are externally brokered using SOAP broker. 
* **provider name**: The of the project that exposes this api 
* **service name**: the target service name within the WS provider (e.g. "Echo" or "GetCustomerDetails") 
* **service major version**: major version number (usually from the wsdl) 
* **service minor version**: minor&nbsp;version number (usually 0)

### security

The Web Service Consumer endpoint must be accessed using credentials (username and password) with the HTTP Basic scheme.

## programming model

Your application must handle correctly the JNDI prefix declared in your Web Service Consumer interface. In order to consume the web service, the application must retrieve by JNDI lookup the following fields:

* `{jndiPrefix}.url`: WS URL endpoint in the WSOI broker 
* `{jndiPrefix}.username`: mandatory username to access the endpoint service 
* `{jndiPrefix}.password`: mandatory password to access the endpoint service

