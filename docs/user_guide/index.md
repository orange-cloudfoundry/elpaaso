# El PaaSo overview

## Goal

The goal of El PaaSo is to ease the build-to-run transition, by automating the application deployment in the different phases of a given app release (development, acceptance testing, pre-production or production environment).
 
Users specify the architecture for the application, which the system uses as template for reproductibly instanciating the application multiple times and driving upgrades/rollbacks. 

## interacting with El PaaSo

The main way to use El PaaSo is through the following flow in the web UI:

* declaring an application
* creating a release of an application
* specifying the logical architecture (see-below) of a release
* instantiating new environments for a release (for development, testing, pre-production or production purpose)
* managing these environments (stop, start, access to logs and metrics, delete ...)

The [UI overview](web_ui_overview.md) illustrate this workflow through UI screenshots.

The [SOAP API](north_api.md) is also available for automation or providing other alternative UIs.

## the logical architecture and service catalog

The [logical architecture](logical_architecture.md) is a set of combined services describing the internal and external needs of the application. 

![a simplified logical architecture](sample_logical_architecture.png)

a sample logical architecture

