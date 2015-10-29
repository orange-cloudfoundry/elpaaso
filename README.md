# Introduction

ElPaaso is an experimental app templating add-on to cloudfoundry. It aims at integrating specifics of an organization through the following features:
* versionned app templates
  * artefacts fetched from a corporate java maven repo
  * app configuration contract
* organization specific meta service catalog 
* organization specific meta-data (cost center, application code, ...)
   
More details into the related cf-summit "Case Study: Orange Labs & Cloud Foundry" talk:

[![Overview of ElPaaso goals through CfSummit 2015 session](https://cloud.githubusercontent.com/assets/4748380/9734992/bafdcdb4-5637-11e5-82e1-6a18d10776ec.png)](http://fr.slideshare.net/gberche/orange-case-study-48927985)

# Sub repos

This is ElPaaSo umbrella repository. It contains some documentation and links to sub-projects:
* [elpaaso-core](https://github.com/Orange-OpenSource/elpaaso-core) UI and core engine  [![Build Status](https://travis-ci.org/Orange-OpenSource/elpaaso-core.svg?branch=master)](https://travis-ci.org/Orange-OpenSource/elpaaso-core)
* [elpaaso-brokers](https://github.com/Orange-OpenSource/elpaaso-brokers) custom service brokers [![Build Status](https://travis-ci.org/Orange-OpenSource/elpaaso-brokers.svg?branch=master)](https://travis-ci.org/Orange-OpenSource/elpaaso-brokers)
* [elpaaso-system-test-apps](https://github.com/Orange-OpenSource/elpaaso-system-test-apps) apps used for automated system tests  [![Build Status](https://travis-ci.org/Orange-OpenSource/elpaaso-system-test-apps.svg?branch=master)](https://travis-ci.org/Orange-OpenSource/elpaaso-system-test-apps)
* [elpaaso-wsdl](https://github.com/Orange-OpenSource/elpaaso-wsdl) WSDL contract for SOAP API  [![Build Status](https://travis-ci.org/Orange-OpenSource/elpaaso-wsdl.svg?branch=master)](https://travis-ci.org/Orange-OpenSource/elpaaso-wsdl)
* [elpaaso-plugins-management](https://github.com/Orange-OpenSource/elpaaso-plugins-management) common maven plugin config shared among repos [![Build Status](https://travis-ci.org/Orange-OpenSource/elpaaso-plugins-management.svg?branch=master)](https://travis-ci.org/Orange-OpenSource/elpaaso-plugins-management)
* [elpaaso-sandbox-ui](https://github.com/Orange-OpenSource/elpaaso-sandbox-ui)
* [elpaaso-sandbox-service](https://github.com/Orange-OpenSource/elpaaso-sandbox-service)

Pending subrepos yet to publish:
* elpaaso-samples

The artefact binaries are stored on:
* release are on https://bintray.com/elpaaso
* snapshots are on [oss.jfrog.org](https://oss.jfrog.org/webapp/#/artifacts/browse/tree/search/quick/eyJzZWFyY2giOiJxdWljayIsInNlbGVjdGVkUmVwb3NpdG9yaWVzIjpbXSwicXVlcnkiOiJlbHBhYXNvKiJ9)


# Deploying and operating ElPaaso 

An ElPaaso instance is made up the following services:
* Identity:
   * LDAP (*): Elpaaso stores user identities along with roles (paas-user or paas-ops)
   * [PWM](https://github.com/jrivard/pwm) (*): password self service application for LDAP directories
* Elpaaso-ui 
* ElPaaso service brokers
* Dependencies on external systems 
   * A CF instance 
   * A java maven repo
   * Orange Dbaas (pg +mysql) (optional, not yet published)

(*) not yet packaged in this repo.   

## Bootstrapping
   
Work is planned to fully automate ElPaaso bootstrapping process through a bosh release (with errands pushing 12 factor compatible services to CF).

For now, services are packaged as spring boot apps that need to be pushed on CF using CLI. Release binaries are published on bintray (see above). Each sub repo describes the expected/supported config env vars.  

## Further dogfooding upgrades

Once a bootstrap elpaaso instance is up, it may be used to instanciate, and upgrade other elpaaso instances (cf [dogfooding arch](https://github.com/Orange-OpenSource/elpaaso-core/blob/109a6a09f71832d76ca165a59653cfe77e92d9cf/cloud-paas/cloud-paas-logical-model/src/main/java/com/francetelecom/clara/cloud/logicalmodel/samplecatalog/ElPaaSoTomcatLogicalModelCatalog.java#L42) or [screenshot](user_guide/elpaaso_dogfooding_arch.png)). 

# Building and contributing to ElPaaso 

All modules build using apache maven, see individual repos for details on how to run unit and integration tests.

## Architecture and design

See [data model](http://fr.slideshare.net/gberche/orange-case-study-48927985/28), [architecture block diagram](http://fr.slideshare.net/gberche/orange-case-study-48927985/29)

Further details in the elpaaso-core javadoc (pending publication of the html rendering, entry point in [overview.html](https://rawgit.com/Orange-OpenSource/elpaaso-core/master/src/main/javadoc/overview.html))

