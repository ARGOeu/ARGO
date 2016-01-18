# ARGO ![ARGO LOGO](http://argoeu.github.io/shared/images/argo-logo.png)

## Availability and reliability monitoring for e-Infrastructures

ARGO is a flexible and scalable framework for monitoring status, availability and reliability of services provided by infrastructures with medium to high complexity. It can generate multiple reports using customer defined profiles (e.g. for SLA management, operations etc) and has built-in multi-tenant support in the core framework.

ARGO Supports flexible deployment models and its modular design enables ARGO to integrate with external systems (such as CMDBs, Service Catalogs etc). During the report generation, ARGO can take into account custom factors such as the importance of a specific service endpoint, scheduled or unscheduled downtimes etc.

## ARGO Modular Architecture

For the Availability & Reliability monitoring, ARGO relies on a modular architecture comprised of the following components:

- [The ARGO Monitoring Engine](https://github.com/ARGOeu/argo-nagios-egi)

  For status monitoring, ARGO relies on Nagios. All probes developed for ARGO follow the Nagios conventions and can run on any stock Nagios box. ARGO provides an optional set of addons for the stock Nagios that provide features such as auto-configuration from external information sources, publishing results to external Message Brokers etc

- [The ARGO Connectors](https://github.com/ARGOeu/argo-egi-connectors) <img src="https://jenkins.argo.grnet.gr/static/3c75a153/images/headshot.png" alt="Jenkins" width="25"/> [![Build Status](https://jenkins.argo.grnet.gr/job/argo-egi-connectors_devel/badge/icon)](https://jenkins.argo.grnet.gr/job/argo-egi-connectors_devel)

  Through the use of custom connectors, ARGO can connect to multiple external Configuration Management Databases and Service Catalogs. Already there are connectors for the EGI and EUDAT e-Infrastructures.

- [The ARGO Consumer](https://github.com/ARGOeu/argo-egi-consumer) <img src="https://jenkins.argo.grnet.gr/static/3c75a153/images/headshot.png" alt="Jenkins" width="25"/> [![Build Status](https://jenkins.argo.grnet.gr/job/argo-egi-consumer_devel/badge/icon)](https://jenkins.argo.grnet.gr/job/argo-egi-consumer_devel)

  The ARGO Consumer is ingesting monitoring results in real-time from external Message Brokers. The consumer is responsible for the initial prefiltering of the monitoring results and encodes them using AVRO serialization format before passing to the Compute Engine.

- [The ARGO Compute Engine](https://github.com/ARGOeu/argo-compute-engine) <img src="https://jenkins.argo.grnet.gr/static/3c75a153/images/headshot.png" alt="Jenkins" width="25"/> [![Build Status](https://jenkins.argo.grnet.gr/job/argo-compute-engine_devel/badge/icon)](https://jenkins.argo.grnet.gr/job/argo-compute-engine_devel) ![Test Coverage](http://jenkins.argo.grnet.gr:9913/jenkins/c/http/jenkins.argo.grnet.gr/job/argo-compute-engine_devel)

  A powerful and scalable analytics engine built on top of Hadoop and HDFS. The Compute Engine is responsible for the aggregation of the status results and the computation of availability and reliability of composite services using customer defined algorithms.

- [The ARGO Web API](https://github.com/ARGOeu/argo-web-api) <img src="https://jenkins.argo.grnet.gr/static/3c75a153/images/headshot.png" alt="Jenkins" width="25"/> [![Build Status](https://jenkins.argo.grnet.gr/job/argo-web-api_devel/badge/icon)](https://jenkins.argo.grnet.gr/job/argo-web-api_devel) ![Test Coverage](http://jenkins.argo.grnet.gr:9913/jenkins/c/http/jenkins.argo.grnet.gr/job/argo-web-api_devel)

  The ARGO Web API provides the Serving Layer of ARGO. It is comprised of a high performance and scalable datastore and a multi-tenant REST HTTP API, which is used for retrieving the Status, Availability and Reliability reports and the actual raw metric results.
  
- [The ARGO Web UI](https://github.com/ARGOeu/argo-egi-web)

  The default web UI is based on the [Lavoisier Data Aggregation Framework](http://software.in2p3.fr/lavoisier/).

The source code for each ARGO component is maintained in separate git repositories under the [ARGOeu organization](https://github.com/ARGOeu/)

## Cluster vs Standalone version

ARGO comes in two flavors:
- a standalone version for deployment in low density e-Infrastructures with a limited number of services

  See the [installation guide for the standalone version](http://argoeu.github.io/guides/installation/)

- a cluster version for deployment in high density e-Infrastructures with a large number of services

    See the [installation guide for the cluster version](http://argoeu.github.io/guides/installation_cluster/)

## Credits

ARGO is developed by [GRNET](http://www.grnet.gr), [SRCE](http://www.srce.unizg.hr/) and [CNRS](http://www.cnrs.fr)

![GRNET](http://argoeu.github.io/shared/images/grnet_transparent.png) ![CNRS](http://argoeu.github.io/shared/images/cnrs.png) ![SRCE](http://argoeu.github.io/shared/images/srce.png)
