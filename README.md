## acme-subsystem

Example for extending WildFly(https://docs.jboss.org/author/display/WFLY8/Extending+WildFly+8)

## Build

Install Maven 3.x and Java 1.7 or higher, enter the following commands:

~~~
$ git clone git@github.com:jbosschina/acme-subsystem.git
$ cd acme-subsystem
$ mvn clean install
~~~

you will find distribution `acme-subsystem-dist.zip` under "target" directory once the build is completed.


## Install & Run

* Assuming a [WildFly](http://wildfly.org/) was installed. Unzip the distribution as below to install `acme-subsystem`

~~~
$ unzip acme-subsystem-dist.zip -d wildfly-8.2.0.Final
~~~

* Run the `acme-subsystem` in [WildFly](http://wildfly.org/):

~~~
$ ./bin/standalone.sh -c standalone-wildfly82.xml
~~~

* The following CLI commands can be used manage `acme-subsystem`

~~~
/subsystem=tracker:read-resource(recursive=true)
/subsystem=tracker/type=war:read-resource(recursive=true)
/subsystem=tracker/type=war:read-attribute(name=tick)
/subsystem=tracker/type=war:write-attribute(name=tick,value=1000)
~~~

* Deploy a war to a [WildFly](http://wildfly.org/) which `acme-subsystem` be installed, the following log output in console:

~~~
12:31:10,511 INFO  [stdout] (Thread-64) Current deployments deployed while war tracking active:
12:31:10,512 INFO  [stdout] (Thread-64) [example.war]
12:31:10,513 INFO  [stdout] (Thread-64) Cool: 0
~~~
