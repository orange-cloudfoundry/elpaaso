# El PaaSo

ElPaaso is an add-on to cloudfoundry that provides the following features to integrate cloudfoundry into organization specifics:
* versionned app templates
* organization specific meta service catalog 
* organization specific meta-data (cost center, application code, ...)
* common operations
  * fetch artefacts from a corporate java maven repo
  * app configuration contract
  * logs
   
More details into the related cf-summit "Case Study: Orange Labs & Cloud Foundry" talk:

![screenshot1235](https://cloud.githubusercontent.com/assets/4748380/9734992/bafdcdb4-5637-11e5-82e1-6a18d10776ec.png)
[![Overview of ElPaaso goals through CfSummit 2015 session](https://cloud.githubusercontent.com/assets/4748380/9734992/bafdcdb4-5637-11e5-82e1-6a18d10776ec.png)](http://fr.slideshare.net/gberche/orange-case-study-48927985)

# Sub repos

This is ElPaaSo umbrella repository. It contains some documentation and links to sub-projects:
* [elpaaso-core](https://github.com/Orange-OpenSource/elpaaso-core) Elpaaso soft  [![Build Status](https://travis-ci.org/Orange-OpenSource/elpaaso-core.svg?branch=master)](https://travis-ci.org/Orange-OpenSource/elpaaso-core)
* [elpaaso-wsdl](https://github.com/Orange-OpenSource/elpaaso-wsdl) WSDL contract for SOAP API  [![Build Status](https://travis-ci.org/Orange-OpenSource/elpaaso-wsdl.svg?branch=master)](https://travis-ci.org/Orange-OpenSource/elpaaso-wsdl)
* [elpaaso-system-test-apps](https://github.com/Orange-OpenSource/elpaaso-system-test-apps) apps used for automated system tests  [![Build Status](https://travis-ci.org/Orange-OpenSource/elpaaso-system-test-apps.svg?branch=master)](https://travis-ci.org/Orange-OpenSource/elpaaso-system-test-apps)
* [elpaaso-plugins-management](https://github.com/Orange-OpenSource/elpaaso-plugins-management) Common maven plugin config shared among repos [![Build Status](https://travis-ci.org/Orange-OpenSource/elpaaso-plugins-management.svg?branch=master)](https://travis-ci.org/Orange-OpenSource/elpaaso-plugins-management)
* [elpaaso-brokers](https://github.com/Orange-OpenSource/elpaaso-brokers)  [![Build Status](https://travis-ci.org/Orange-OpenSource/elpaaso-brokers.svg?branch=master)](https://travis-ci.org/Orange-OpenSource/elpaaso-brokers)

The artefact binaries are stored on:
* release are on https://bintray.com/elpaaso
* snapshots are on [oss.jfrog.org](https://oss.jfrog.org/webapp/#/artifacts/browse/tree/search/quick/eyJzZWFyY2giOiJxdWljayIsInNlbGVjdGVkUmVwb3NpdG9yaWVzIjpbXSwicXVlcnkiOiJlbHBhYXNvKiJ9)

Pending repositories not yet available :
* elpaaso-samples

# 

TODOs: 
* add pointer to Cf summit videos + slides
* design docs

