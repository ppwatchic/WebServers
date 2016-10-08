## Goal
Deploy a war file into tomcat's webapps folder.

## Reference
[Install tomcat 8](https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-8-on-ubuntu-16-04). 

## Issue  
### Start tomcat 
1. To start tomcat using this command:`sudo systemctl start tomcat`.   
2. Result from the said command: 
**Job for tomcat.service failed because the control process exited with error code. 
See "systemctl status tomcat.service" and "journalctl -xe" for details.**   
3. Run the command `journalctl -xe` to view details:
```
-- Defined-By: systemd  
-- 
-- Unit tomcat.service has begun starting up.
Oct 08 14:28:13 pingping systemd[17167]: tomcat.service: Failed at step EXEC spawning /opt/tomcat/bin/startup.sh: Perm
-- Subject: Process /opt/tomcat/bin/startup.sh could not be executed
-- Defined-By: systemd
-- 
-- The process /opt/tomcat/bin/startup.sh could not be executed and failed.
-- 
-- The error number returned by this process is 13.
Oct 08 14:28:13 pingping-X450CC systemd[1]: tomcat.service: Control process exited, code=exited status=203
Oct 08 14:28:13 pingping-X450CC systemd[1]: Failed to start Apache Tomcat Web Application Container.
-- Subject: Unit tomcat.service has failed
-- Defined-By: systemd
-- 
-- Unit tomcat.service has failed.
-- 
-- The result is failed.
Oct 08 14:28:13 pingping-X450CC systemd[1]: tomcat.service: Unit entered failed state.
Oct 08 14:28:13 pingping-X450CC systemd[1]: tomcat.service: Failed with result 'exit-code'.
```     
4. Check who is using port 8080 using command: `grep 8080 /ect/services` and getting following:     
`http-alt	8080/tcp	webcache	# WWW caching service  
http-alt	8080/udp`.  
5. Finally, remove tomcat.   
6. Reinstall tomcat. Still doesn't work.   
7. Finally [this one](http://unix.stackexchange.com/questions/235891/tomcat-8-will-not-start-after-initial-install) help: 
7.1 giving tomcat user ownership of the whole tomcat directory:  
`cd /opt && sudo chown -R tomcat tomcat/`  
7.2 and commenting out below line in /etc/systemd/system/tomcat.service:  
Environment='CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC'.  

## Bingo


