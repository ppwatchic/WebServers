1. The following error happens: 
Encountered exception org.apache.catalina.LifecycleException: Failed to start component [StandardEngine[Catalina].StandardHost[localhost].StandardContext[/webapp-0.0.1-SNAPSHOT]].  
2. You have a version conflict, please verify whether compiled version and JVM of Tomcat version are same. you can do it by examining tomcat startup .bat , looking for JAVA_HOME
