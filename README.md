# Cloudinsight supported dockerized service examples

This repository demostrate how to configure oneapm-ci-agent when using docker to run oneapm-ci-agent, and how to configure specific service in order to use oneapm-ci-agent.

For each service docker-related configuration locates in correspond directory(not exist if no configuration need), and oneapm-ci-agent related configuration examples are in conf.d directory.

If you want to see the result how one special service looks on Oneapm Cloud Insight web page, try type

```
$ ./docker-compose up -d
```

and visit cloud.oneapm.com.


## Few things need to note if you try the command above

* Servial common services are enabled by default, may pull some big image and do some build before the whole thing running, so be patient.
* It would be better if you have basic acknowledgement of how docker-compose works and basic yaml syntax.
* By default all support servcies will pull correspond image (if image not exists) and run, comment the service section and correspond link item of oneapm section you don't want to run in the docker-compose.yaml, like the 'demo' section, and at the mean time don't forget to suffix the correspond SERVICE.yaml with '.example' under the conf.d/ directory .
* Provide your own LICENSE_KEY to replace oneapm:LICENSE_KEY.
* Some services like solr need to populate data in order to apper on the platform list.

## Known issues

* If most of the serices you don't need are not commented, the ci agent will spend a lot of 'time out' time to connect nonexist service. Better to suffix the SERVICE.yaml with '.example' of the conf.d/ directory.
* In some situtation, agent will die because of unknow issue.
* Kafka need topics.
* Mesos slave cluster error.
* Kafka cannot auto create topics when set JMX_PORT environment because JMX_PORT will be used to create another broker,  but JMX_PORT is used.
