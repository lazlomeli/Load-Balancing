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

Go to the ```web1``` IP address specified in the VM config. You should get a Wordpress welcome page. Go next till you get this page:

![Screenshot 2022-11-27 235431](https://user-images.githubusercontent.com/72606659/204164137-644a7ff6-bc07-405b-82af-2394462a83ec.jpg)

Fill up the data as stated in the image and click Submit.

You should get this:

![image](https://user-images.githubusercontent.com/72606659/204164182-f6ed9f92-13c7-4d6f-b15f-d26beedad983.png)

Copy this information and get back the ```Vagrant Architecture``` folder, there, go in the ```wordpress``` folder and create a file called ```wp-config.php```. Paste the information in this file.

> Keep in mind you could automatically do this by using the ```sed``` command in the VM's Vagrantfile (```sed -i "s/username/wp_user/g" wp_config.php``` and so on, in this tutorial I will do it manually since it works better)

After this, create an actual account to manage the dashboard and after logging in, you should have a fully functioning Wordpress Dashboard.

<br />

_________

## 3.1 Configuring HAProxy to view the VM's statistics

We will start by closing ```web1``` and ```db``` virtual machines using ```vagrant halt web1``` and the same with ```db```. We do this to not melt our RAM.

After it, do ```vagrant up lb``` to bring up the load balancing VM.

Now, we will configure ```haproxy.cfg``` file. To do so, go to ```/etc/haproxy/``` and do ```sudo nano haproxy.cfg``` to edit the file.

