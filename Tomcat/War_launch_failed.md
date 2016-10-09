1. The following error happens: 
Encountered exception org.apache.catalina.LifecycleException: Failed to start component [StandardEngine[Catalina].StandardHost[localhost].StandardContext[/webapp-0.0.1-SNAPSHOT]].  
2. You have a version conflict, please verify whether compiled version and JVM of Tomcat version are same. you can do it by examining tomcat startup .bat , looking for JAVA_HOME.   
2.1 To check JVM version of Tomcat, type this command: `ps -ef | grep tomcat` and you can see the path of JDK.   
To chekc the detailed version, follow by this command `java -version`.  
2.2 To check JVM version of war, go to project's pom.xml and also properties.   
2.3 And I believe that they have same version.   
2.4 Now have to find another way.  
3. 


