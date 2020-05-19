I discovered a run time error at wildfly 19.1.x quickstart jaxrs-client wnen running the Arquillian Tests.
$ cd jaxrs-client
$ mvn clean verify -Parq-remote
...
[ERROR] requestResponseFiltersTest(org.jboss.as.quickstarts.jaxrsclient.test.ContactsRestClientIT)  Time elapsed: 0.325 s  <<< ERROR!
java.lang.NoClassDefFoundError: org/apache/commons/logging/LogFactory
	at org.jboss.as.quickstarts.jaxrsclient.test.ContactsRestClientIT.requestResponseFiltersTest(ContactsRestClientIT.java:218)
Caused by: java.lang.ClassNotFoundException: org.apache.commons.logging.LogFactory
	at org.jboss.as.quickstarts.jaxrsclient.test.ContactsRestClientIT.requestResponseFiltersTest(ContactsRestClientIT.java:218)

My environment are:
JBoss EAP-7.3.0

$ mvn -version
Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
Maven home: /home/tc/maven/apache-maven-3.6.3
Java version: 1.8.0_251, vendor: Oracle Corporation, runtime: /home/tc/jdk/jdk1.8.0_251/jre
Default locale: en_CA, platform encoding: UTF-8
OS name: "linux", version: "4.10.0-38-generic", arch: "amd64", family: "unix"

I fixed by adding dependency to the pom.xml for quickstart jaxrs-client.
I forked and cloned the wildfly quickstart repository, checkouted code from the latest develop branch, committed  work on my topic branch, created a pull request from my fork.

I submitted my pull request back to the latest develop branch:
https://github.com/wildfly/quickstart/pull/427

It was pending for review.
