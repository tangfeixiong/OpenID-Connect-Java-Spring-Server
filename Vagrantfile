# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  #; refer to https://app.vagrantup.com/centos/boxes/7/versions/1902.01
  # config.vm.box = "centos/7"
  # config.vm.box_version = "1902.01"
  # config.vm.box = "centos-7-cloud"
  # config.vm.box_url = ["https://cloud.centos.org/centos/7/vagrant/x86_64/images/CentOS-7.box",
  #       "https://cloud.centos.org/centos/7/vagrant/x86_64/images/CentOS-7-x86_64-Vagrant-1910_01.VirtualBox.box"]
  #; refer to https://app.vagrantup.com/ubuntu/boxes/bionic64/versions/20190212.1.0
  # config.vm.box = "ubuntu/bionic64"
  # config.vm.box_version = "20190212.1.0"
  config.vm.box = "ubuntu-18.04-server-cloud"
  config.vm.box_url = ["https://cloud-images.ubuntu.com/releases/18.04/release/ubuntu-18.04-server-cloudimg-amd64-vagrant.box",
        "https://cloud-images.ubuntu.com/releases/bionic/release-20191114/ubuntu-18.04-server-cloudimg-amd64-vagrant.box"]

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest: 8080, host: 19080
  config.vm.network "forwarded_port", guest: 443, host: 19443

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.network "private_network", type: "dhcp"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.synced_folder "/Users/fanhongling/Downloads", "/Users/fanhongling/Downloads"
  config.vm.synced_folder "/Users/fanhongling/go", "/Users/fanhongling/go"
  #; Microsoft Windows
  # config.vm.synced_folder "f:/", "/windows_drive_f"
  # config.vm.synced_folder "g:/", "/windows_drive_g"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.
  config.vm.provider "virtualbox" do |vb, override|
    vb.cpus = "2"
    vb.memory = "4096"

    #override.ssh.insert_key = false
    #override.vm.base_mac = "08002708697F"
  end  

  config.ssh.insert_key = false

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
  config.vm.provision "centos-openjdk", type: "shell", run: "never" do |s|
    s.inline = "yum install "
  end

  config.vm.provision "ubuntu-bootstrap", type: "shell", run: "never", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y ifupdown"
  SHELL

  config.vm.provision "ubuntu-openjdk", type: "shell", run: "never", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install default-jdk
    # sudo apt install default-jdk-headless
    # sudo apt-get install openjdk-8-jdk"
    # sudo apt-get install default-jre
    # sudo apt-get install openjdk-11-jre-headless"
  SHELL

  #; https://github.com/dotless-de/vagrant-vbguest
  # we will try to autodetect this path. 
  # However, if we cannot or you have a special one you may pass it like:
  # config.vbguest.iso_path = "#{ENV['HOME']}/Downloads/VBoxGuestAdditions.iso"
  # or an URL:
  # config.vbguest.iso_path = "http://company.server/VirtualBox/%{version}/VBoxGuestAdditions.iso"
  # or relative to the Vagrantfile:
  # config.vbguest.iso_path = "../relative/path/to/VBoxGuestAdditions.iso"
  
  # set auto_update to false, if you do NOT want to check the correct 
  # additions version when booting this machine
  config.vbguest.auto_update = false
  
  # do NOT download the iso file from a webserver
  config.vbguest.no_remote = true

end
