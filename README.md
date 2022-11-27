# Load Balancing Architecture with Vagrant and Docker
![version](https://img.shields.io/badge/version-1.0-blue)

**@author:** Lazlo Meli \< https://github.com/lazlomeli >

> Built with: 

![Vagrant](https://img.shields.io/badge/vagrant-%231563FF.svg?style=for-the-badge&logo=vagrant&logoColor=white)
![Ruby](https://img.shields.io/badge/ruby-%23CC342D.svg?style=for-the-badge&logo=ruby&logoColor=white)
![WordPress](https://img.shields.io/badge/WordPress-%23117AC9.svg?style=for-the-badge&logo=WordPress&logoColor=white)
![Shell Script](https://img.shields.io/badge/shell_script-%23121011.svg?style=for-the-badge&logo=gnu-bash&logoColor=white)
![Oracle](https://img.shields.io/badge/Oracle-F80000?style=for-the-badge&logo=oracle&logoColor=white)
![MySQL](https://img.shields.io/badge/mysql-%2300f.svg?style=for-the-badge&logo=mysql&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)

<br />

_________

1. Dependencies 

- Have [Docker and Docker Desktop](https://www.docker.com/) installed.

- Have [Vagrant](https://www.vagrantup.com/) installed.

<br />

_________

### 2. Installation
Clone the repostory in your desired folder. After doing so, `git pull` just to make sure you have the latest version.

<br />

_________

## 3. Running the Vagrant Architecture

First off go into the ```Vagrant Architecture``` directory. We are going to need the latest Wordpress installation files for this architecture to work, so we will download them with the following command: ```wget http://wordpress.org/latest.tar.gz```.

Unzip it with ```tar xzf latest.tar.gz```. You should end up with a directory full of files called ```wordpress```.

Take a look at the Vagrantfile in the directory. There are four different virtual machines in it: ```web1```, ```web2```, ```db``` and ```lb```. We will start by using the command ```vagrant up web1``` to bring up this VM. After it's done, do the same with the ```db``` VM.

Go to the ```web1``` IP address specified in the VM config. You should get this:



