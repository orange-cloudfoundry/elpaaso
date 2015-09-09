# Introduction

ElPaaso is an add-on to cloudfoundry that provides the following features to integrate cloudfoundry into organization specifics:
* versionned app templates
* organization specific meta service catalog 
* organization specific meta-data (cost center, application code, ...)
* common operations
  * fetch artefacts from a corporate java maven repo
  * app configuration contract
  * logs
   
More details into the related cf-summit "Case Study: Orange Labs & Cloud Foundry" talk:

[![Overview of ElPaaso goals through CfSummit 2015 session](https://cloud.githubusercontent.com/assets/4748380/9734992/bafdcdb4-5637-11e5-82e1-6a18d10776ec.png)](http://fr.slideshare.net/gberche/orange-case-study-48927985)

# Sub repos

This is ElPaaSo umbrella repository. It contains some documentation and links to sub-projects:
* [elpaaso-core](https://github.com/Orange-OpenSource/elpaaso-core) UI and core engine  [![Build Status](https://travis-ci.org/Orange-OpenSource/elpaaso-core.svg?branch=master)](https://travis-ci.org/Orange-OpenSource/elpaaso-core)
* [elpaaso-brokers](https://github.com/Orange-OpenSource/elpaaso-brokers) custom service brokers [![Build Status](https://travis-ci.org/Orange-OpenSource/elpaaso-brokers.svg?branch=master)](https://travis-ci.org/Orange-OpenSource/elpaaso-brokers)
* [elpaaso-system-test-apps](https://github.com/Orange-OpenSource/elpaaso-system-test-apps) apps used for automated system tests  [![Build Status](https://travis-ci.org/Orange-OpenSource/elpaaso-system-test-apps.svg?branch=master)](https://travis-ci.org/Orange-OpenSource/elpaaso-system-test-apps)
* [elpaaso-wsdl](https://github.com/Orange-OpenSource/elpaaso-wsdl) WSDL contract for SOAP API  [![Build Status](https://travis-ci.org/Orange-OpenSource/elpaaso-wsdl.svg?branch=master)](https://travis-ci.org/Orange-OpenSource/elpaaso-wsdl)
* [elpaaso-plugins-management](https://github.com/Orange-OpenSource/elpaaso-plugins-management) common maven plugin config shared among repos [![Build Status](https://travis-ci.org/Orange-OpenSource/elpaaso-plugins-management.svg?branch=master)](https://travis-ci.org/Orange-OpenSource/elpaaso-plugins-management)

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
For now, services are packaged a spring boot app that need to be pushed on CF. Release binaries are published on bintray (see above). Each sub repo describes the expected/supported config.  

## Further dogfooding upgrades

Once a bootstrap elpaaso instance is up, it may be used to instanciate, and upgrade other elpaaso instances. 

# Building and contributing to ElPaaso 

All module build using apache maven, see individual repos for details on how to run unit and integration tests.

## Architecture and design

See [data model](http://fr.slideshare.net/gberche/orange-case-study-48927985/18), [architecture block diagram](See [data model](http://fr.slideshare.net/gberche/orange-case-study-48927985/19)

Further details in the elpaaso-core javadoc (pending publication of the html rendering, entry point in [overview.html](https://rawgit.com/Orange-OpenSource/elpaaso-core/master/src/main/javadoc/overview.html))

