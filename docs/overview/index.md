# El PaaSo overview

### definition of El PaaSo

The goal of El PaaSo is to help developers in deploying their applications by automating their deployment. 
This is achieved by specifying the architecture for the application, which is used as template for instanciating the application multiple times across build/run cycles (development, testing, pre-production or production environment). 

ElPaaso ensures reproductibility of deployment in these phases

In summary, elpaaso users only have to manage:

* their code (the application itself),
* their data (application data),

While the PaaS provides:

* the provisionning of technical resources (cf apps, routes)
* the subscription of required common services (e.g. monitoring, inventory)
* the deployment and configuration of the application (through env vars)
* application monitoring and log management.


## interacting with El PaaSo

The main way to use El PaaSo is through a web UI that offers the following features:

* declaring an application,
* creating a release of an application,
* defining a logical architecture (see-below) for a version
* instantiating new environments based on previously generated templates (for development, testing, pre-production or production purpose)
* managing these environments (stop, start, delete, access to logs and metrics...)

The [web portal overview](web_portal_overview.md) offers some screenshots and videos explaining how to use the web portal.

## the logical architecture

The [logical architecture](logical_architecture.md) is a set of combined services to describe the internal and external needs of the application. Defining a logical architecture consists in determining the number of execution nodes, to associate them logical services specifying with additional functional or technical parameters.

![a simplified logical architecture](sample_logical_architecture.png)
a sample logical architecture

