#  **<span style="color:green">Xashy Tech</span>**
### **<span style="color:green">Contacts: +12023676985<br> WebSite : <https://xashyinc.com/></span>**
### **Email: info@xashyinc.com.com**

## Apache Tomcat Installation And Setup In AWS EC2 Redhat Instance.
##### Prerequisite
+ AWS Acccount.
+ Create Redhat EC2 T2.micro Instance.
+ Create Security Group and open Tomcat ports or Required ports.
   + 8080 ..etc
+ Attach Security Group to EC2 Instance.
+ Install java openJDK 1.8+

### Install Java JDK 1.8+ 

``` sh
# change hostname to tomcat
sudo hostnamectl set-hostname tomcat
sudo su - ec2-user
cd /opt 
# install Java JDK 1.8+ as a pre-requisit for tomcat to run.
sudo yum install git wget -y
sudo yum install java-1.8.0-openjdk-devel -y
# install wget unzip packages.
sudo yum install wget unzip -y
```
## Install Tomcat version 9.0.75
### Download and extract the tomcat server
``` sh
sudo wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.76/bin/apache-tomcat-9.0.76.tar.gz
sudo tar -xf apache-tomcat-9.0.76.tar.gz
sudo rm -rf apache-tomcat-9.0.76.tar.gz
### rename tomcat for good naming convention
sudo mv apache-tomcat-9.0.76 tomcat9  
### assign executable permissions to the tomcat home directory
sudo chmod 777 -R /opt/tomcat9
sudo chown ec2-user -R /opt/tomcat9
### start tomcat
sh /opt/tomcat9/bin/startup.sh
# create a soft link to start and stop tomcat
# This will enable us to manage tomcat as a service
sudo ln -s /opt/tomcat9/bin/startup.sh /usr/bin/starttomcat
sudo ln -s /opt/tomcat9/bin/shutdown.sh /usr/bin/stoptomcat
starttomcat
sudo su - ec2-user


vi /opt/tomcat9/webapps/manager/META-INF/context.xml
# Find the following line within the document:  allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
# Edit this line to show this:  allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1 |.*" />

vi /opt/tomcat9/conf/tomcat-users.xml
# Edit this file and add the following lines just before tag "</tomcat-users>"
<role rolename="admin-gui,manager-gui"/> 
<user username="admin" password="tomhost@80" roles="admin-gui,manager-gui"/>





scp -i key target/*war ec2-user@172.31.64.214:/opt/tomcat9/webapps

```















