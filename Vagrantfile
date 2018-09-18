# -*- mode: ruby -*-
# vi: set ft=ruby :
#########################################################
###This Vagrantfile has been tested with bento/centos-7.3 however it should work with most of CentOS 6.x and 7.x vagrant boxes.
###You need to make appropriate changes to installation commands if you are using an Ubuntu box.
###You also need to make changes to network settings (Private/Public/IP address range) as per your lab settings.
###Happy learning!!!
#########################################################
$script = <<SCRIPT

#!/bin/sh
echo "----Installing Utilities!!!!----"
echo "-------------------------------------"
echo "-------------------------------------"
echo "-------------------------------------"
sudo yum check-update
sudo yum install -y tree telnet curl elinks
echo "-------------------------------------"
echo "-------------------------------------"
echo "-------------------------------------"
echo "----Installing GIT and Jenkins!!!!----"
echo "-------------------------------------"
echo "-------------------------------------"
echo "-------------------------------------"
sudo yum install git -y
sudo yum install java-1.8.0-openjdk.x86_64 -y
sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo
sudo rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
sudo yum install jenkins -y
echo "----Start and enable Jenkins service!!!!----"
sudo systemctl enable jenkins
sudo systemctl start jenkins
echo "-------------------------------------"
echo "-------------------------------------"
echo "-------------------------------------"
echo "----GIT and Jenkins installation complete!!!!----"
echo "-------------------------------------"
echo "-------------------------------------"
echo "-------------------------------------"
#docker installation script for CentOS 7
echo "----Docker installation starts----"
echo "-------------------------------------"
echo "-------------------------------------"
echo "-------------------------------------"
sudo yum check-update
curl -fsSL https://get.docker.com/ | sh
sudo systemctl start docker
echo "----checking docker service status----"
sudo systemctl status docker
sudo systemctl enable docker
echo "----Enabling Docker Command execution without Sudo----"
sudo usermod -aG docker vagrant
echo "-------------------------------------"
echo "-------------------------------------"
echo "-------------------------------------"
echo "----Docker installation and configuration completed successfully----"
echo "-------------------------------------"
echo "-------------------------------------"
echo "-------------------------------------"

SCRIPT

Vagrant.configure("2") do |config|

config.vm.box = "bento/centos-7.3"
config.vm.hostname = "jupiter"
config.vm.network "private_network", ip: "172.28.28.145"
config.vm.provision "shell", inline: $script

end
