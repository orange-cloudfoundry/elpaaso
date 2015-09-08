# El PaaSo overview

### definition of El PaaSo

The goal of El PaaSo is to help developers in deploying their applications by the automated processing of platforms for each application. This is achieved by requiring the architect of the application to define a logical architecture for the application. The logical architecture controls the automated deployment of the application on a platform that fits the application needs (development, testing, pre-production or production environment). This helps open up the world of build and run by introducing fluidity and continuity between the build, test and run phases.

In summary, you only have to manage:

* your code (the application itself),
* your data (application data),

While the PaaS provides:

* the provisionning of technical resources (in collaboration with the IaaS)
* the subscription of required common services,
* the deployment and configuration of the application,
* application monitoring and log management.

![PaaS different service models in details](paas_service_models_details.png)
PaaS different service models in details

## interacting with El PaaSo

The main way to use El PaaSo is through a web UI that offers the following features:

* declaring an application,
* creating a release of an application,
* defining a logical architecture (see-below),
* starting a projection from the logical architecture to a technical architecture templates (for development, testing, pre-production or production)
* instantiating new environments based on previously generated templates,
* managing these environments.

The [web portal overview](web_portal_overview.md) offers some screenshots and videos explaining how to use the web portal.

## the logical architecture

The [logical architecture](logical_architecture.html) is a set of combined services to describe the internal and external needs of the application. Defining a logical architecture consists in determining the number of execution nodes, to associate them logical services specifying with additional functional or technical parameters.

![a simplified logical architecture](simple_logical_architecture.png)
a simplified logical architecture

The challenge of El PaaSo is not only to configure servers. It is also about converting a software architecture into technical environment, taking care about the constraints related to quality of service (SLA): platform sizing (cpu, memory, storage, number of servers or JVM, disaster recovery plan...) in order to meet the desired performance. Thus the required  resources will be different depending on the type of environment: development, test, pre-prod or prod environment.