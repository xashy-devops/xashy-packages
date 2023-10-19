#  **<span style="color:green">Xashy Tech</span>**
### **<span style="color:green">Contacts: +12023676985<br> WebSite : <https://xashyinc.com/></span>**
### **Email: info@xashyinc.com.com**



## Apache Maven Installation And Setup In AWS EC2 Redhat Instance.
##### Prerequisite
+ AWS Acccount.
+ Create Security Group and open Required ports.
   + 22 ..etc
+ Create Redhat EC2 T2.medium Instance with 4GB of RAM.
+ Attach Security Group to EC2 Instance.
+ Install java openJDK 1.8+

### Change your server hostname to "maven"
``` sh
sudo hostnamectl set-hostname maven
```

### switch to ec2-user and assume the identity priviledges
``` sh
sudo su - ec2-user
```

### change directory to the /opt directory
``` sh
cd /opt
```

### Install Java JDK 11+  and other softares (GIT, wget and tree)
``` sh
sudo yum install wget nano tree unzip git-all -y
```
``` sh
sudo yum install java-11-openjdk-devel java-1.8.0-openjdk-devel -y
```
### Check the java version to confrm that java has been installed successfully
``` sh
java --version
```
### Check the git version to confrm that git has been installed successfully
``` sh
git --version
```

### Download, extract and Install Maven
``` sh
sudo wget https://dlcdn.apache.org/maven/maven-3/3.9.5/binaries/apache-maven-3.9.5-bin.zip
```
### Unzip the maven file
``` sh
sudo unzip apache-maven-3.9.5-bin.zip
```
### delete the zipped maven file
``` sh
sudo rm -rf apache-maven-3.9.5-bin.zip
```
### change the unzipped maven file name to "manven"
``` sh
sudo mv apache-maven-3.9.5/ maven
```

### Set Environmental Variable  - For Specific User eg ec2-user
``` sh
vi ~/.bash_profile  
``` 
### add these lines into the file
``` sh
export M2_HOME=/opt/maven
export PATH=$PATH:$M2_HOME/bin
```
### Refresh the profile file 
``` sh
source ~/.bash_profile
``` 
### Verify if maven is running
``` sh
mvn --version
```

