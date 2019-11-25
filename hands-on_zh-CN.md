# Hands on

## Reference

* [How To Install Java with `apt` on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-18-04)
* [Deploy Application at Tomcat Root](https://www.baeldung.com/tomcat-root-application)

## Linux 

Ubuntu 18.04 (bionic) VM
1. Image: [ubuntu-18.04-server-cloudimg-amd64-vagrant.box](https://cloud-images.ubuntu.com/releases/releases/18.04/release/ubuntu-18.04-server-cloudimg-amd64-vagrant.box)
2. VirtualBox:  https://www.virtualbox.org/wiki/Downloads
3. Vagrant: https://www.vagrantup.com/downloads.html

### Vagrant

Removing outdated image (optional)

    fanhonglingdeMacBook-Pro:OpenID-Connect-Java-Spring-Server fanhongling$ vagrant box list
    ubuntu-18.04-server-cloud (virtualbox, 0)
    
    fanhonglingdeMacBook-Pro:OpenID-Connect-Java-Spring-Server fanhongling$ vagrant box remove ubuntu-18.04-server-cloud
    Box 'ubuntu-18.04-server-cloud' (v0) with provider 'virtualbox' appears
    to still be in use by at least one Vagrant environment. Removing
    the box could corrupt the environment. We recommend destroying
    these environments first:

    default (ID: 054871c91ba842908551bcf8fba435e3)

    Are you sure you want to remove this box? [y/N] y
    Removing box 'ubuntu-18.04-server-cloud' (v0) with provider 'virtualbox'...

Start up from host (for example Mac)

    fanhonglingdeMacBook-Pro:OpenID-Connect-Java-Spring-Server fanhongling$ vagrant up

-> more outputs: [vagrant-command-output.txt](./vagrant-command-output.txt)
  
issue: failed while configuring network interfaces

* ssh vm

    fanhonglingdeMacBook-Pro:OpenID-Connect-Java-Spring-Server fanhongling$ vagrant ssh
    Welcome to Ubuntu 18.04.3 LTS (GNU/Linux 4.15.0-70-generic x86_64)
    ...
    
* init apt-get

    vagrant@ubuntu-bionic:~$ sudo apt-get update
    Get:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
    ...
    
-> more outputs: [apt-get-output.txt](./apt-get-output.txt)

* install

    vagrant@ubuntu-bionic:~$ sudo apt-get install ifupdown
    ...
    
* exit

    vagrant@ubuntu-bionic:~$ exit
    logout
    Connection to 127.0.0.1 closed.

* reload from vagrant

    fanhonglingdeMacBook-Pro:OpenID-Connect-Java-Spring-Server fanhongling$ vagrant reload

### Java

Install OpenJDK

    vagrant@ubuntu-bionic:~$ sudo apt-get install -y default-jdk
    ...
    vagrant@ubuntu-bionic:~$ java -version
    openjdk version "11.0.4" 2019-07-16
    OpenJDK Runtime Environment (build 11.0.4+11-post-Ubuntu-1ubuntu218.04.3)
    OpenJDK 64-Bit Server VM (build 11.0.4+11-post-Ubuntu-1ubuntu218.04.3, mixed mode, sharing)
    vagrant@ubuntu-bionic:~$ javac -version
    javac 11.0.4

Install Maven


## Build

### Maven

For example

    fanhonglingdeMacBook-Pro:OpenID-Connect-Java-Spring-Server fanhongling$ mvn package

-> more outputs: [maven-build-output.txt](./maven-build-output.txt)

### Docker Build


## Deploy

### Deploy the Server Webapp with Jetty into host (e.g. Mac)

More info to see https://github.com/mitreid-connect/OpenID-Connect-Java-Spring-Server/wiki/Build-instructions

    fanhonglingdeMacBook-Pro:OpenID-Connect-Java-Spring-Server fanhongling$ cd openid-connect-server-webapp/
    fanhonglingdeMacBook-Pro:openid-connect-server-webapp fanhongling$ mvn jetty:run-war

-> outputs [maven-deploy-output.txt](./maven-deploy-output.txt)
-> demo ![server-webapp-home.jpg](./server-webapp-home.jpg)
