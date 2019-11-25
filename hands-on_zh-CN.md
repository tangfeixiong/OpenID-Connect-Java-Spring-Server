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

-> outputs [vagrant-up-output.txt](./vagrant-up-output.txt)
  
issue: failed while configuring network interfaces

## Build

### Maven

For example

    fanhonglingdeMacBook-Pro:OpenID-Connect-Java-Spring-Server fanhongling$ mvn package

-> outputs [maven-build-output.txt](./maven-build-output.txt)

### Docker Build


## Deploy

### Deploy the Server Webapp with Jetty into host (e.g. Mac)

More info to see https://github.com/mitreid-connect/OpenID-Connect-Java-Spring-Server/wiki/Build-instructions

    fanhonglingdeMacBook-Pro:OpenID-Connect-Java-Spring-Server fanhongling$ cd openid-connect-server-webapp/
    fanhonglingdeMacBook-Pro:openid-connect-server-webapp fanhongling$ mvn jetty:run-war

-> outputs [maven-deploy-output.txt](./maven-deploy-output.txt)
-> demo ![server-webapp-home.jpg](./server-webapp-home.jpg)
