1. The following error happens: 
Encountered exception org.apache.catalina.LifecycleException: Failed to start component [StandardEngine[Catalina].StandardHost[localhost].StandardContext[/webapp-0.0.1-SNAPSHOT]].  
2. You have a version conflict, please verify whether compiled version and JVM of Tomcat version are same. you can do it by examining tomcat startup .bat , looking for JAVA_HOME.   
 2.1 To check JVM version of Tomcat, type this command: `ps -ef | grep tomcat` and you can see the path of JDK.   
To chekc the detailed version, follow by this command `java -version`.  
 2.2 To check JVM version of war, go to project's pom.xml and also properties.   
 2.3 And I believe that they have same version.   
 2.4 Now have to find another way.  
3. Look into detail about the error, check **/opt/tomcat/logs/catalina.YYYY-MM-DD.log**.  
And there are errors like this one: `nested exception is java.lang.NoClassDefFoundError: com/trello4java/trello/Trello`.  
 3.1 The reason for the above error is some classes are local jar file, not managed by maven repository.  
 3.2 To fix this, I first check the project build path. and the missed jar (trello.jar) is included. 
 3.3 Continue checking properties->Deployment Assembly, the missed jar has this Deploy Path: WEB-INF/lib.
 3.4 Open the war file and check if `WEB-INF/lib` includes the jar file: It didn't include in this war file.
 3.5 To address this issue, manually add the jar file into `WEB-INF/lib`. And then run `mvn package` again. 


