#### Setup EC2 instance with Tomcat8 in AWS - Manually
- Create an EC2 instance, & ssh into it.
- If ssh not connecting, check
VPC—>RT—> Routes tab, ensure that you have a default route pointing to your Internet gateway (IGW).
- If IGW not there, copy IGW ID,if IGW not there create one & attach it to VPC.
- VPC—>RT—> Routes tab—>edit—>Add—>0.0.0.0/0—>Paste the IGW-ID—>save.

-Install Java
[ec2@]$sudo yum install java-1.8.0-openjdk.x86_64
[ec2@]$java -version

-Download Tomcat8
[ec2@]$wget http://download.nextag.com/apache/tomcat/tomcat-8/v8.5.23/bin/apache-tomcat-8.5.23.tar.gz
[ec2@]$tar xzf apache-tomcat-8.5.23.tar.gz    /* to extract archive tar file
[ec2@]ls
[ec2@]$cd apache-tomcat-8.5.23
[ec2@]$./bin/startup.sh      /*to start Tomcat

EC2—>SG—>select SG of running EC2 instance—>Inbound Rules—>Edit—>Custom TCP Rule—>8080—>save
-Copy Public DNS of running instance, goto browser
http:/Paste Public DNS:8080/     /*should open tomcat page  

[ec2@]$./bin/shutdown.sh      /*to stop Tomcat
