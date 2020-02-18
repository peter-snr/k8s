# Kubernetes Getting Started

Getting to know and use kubernetes.  This repository contains code and howto's for getting started with kubernetes.

I recently took a new position where kubernetes is in use and I have the privilege of being able to learn on the job so to speak.  I already have 20+ years of Linux, coding and integration and a start up so I do have some skills :) .

This repository has come alive with links and information I used to get started.  

If you stumble upon this repository via some search engine and decide to give it a try please bear in mind that you will need to understand.

  * The Linux command line and some system admin
  * Docker including swarm.
  * Virtual Machines (vbox)

That will do for now, more to be added...

Software will be open source.

All installed and set up locally using virtual machines.

# Getting Started


A laptop will be used for this research project namely a HP ENVY m6 with a COREi7&tm; processor and 16GB of RAM.  It also has a 1TB SSD disk.  Anything less that this will struggle.

The Operating System is:
```bash
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.3 LTS"
``` 

## Virtual Machines

Install VirtualBox

No description here, lots out there on how to install.  Staying focused on kubernetes...

To make life easy it's a good idea to create a virtual machine that you will use as a 
template for others, then you only have to configure one with all the software etc.  
After that just clone it each time.

I never like to reinvent the wheel, so first check the Web.  
In this case, Stackoverflow (my favourite site), has an interesting entry:- 
[how can i create ubuntu based docker host by using docker machine with virtualbo](https://stackoverflow.com/questions/33935800/how-can-i-create-ubuntu-based-docker-host-by-using-docker-machine-with-virtualbo)

Do not need docker-machine part, anyhow it might get in the way of kubernetes.  Therefore only follow steps 1 to 18. They are reproduced below.

1. Get Ubuntu Server ISO
2. Create a machine in VirtualBox. I called mine "Ubuntu template" because I want to learn Swarm locally, so I want a machine that I'll be able to duplicate and get subsequent machines quickly after the longer initial setup.
3. Enable bridged networking instead of NAT for the machine in the settings
4. Start the machine and install Ubuntu using the ISO. During installation it'll give you an option to install OpenSSH, select that option. It'll also ask you to create a new user. I called mine "ubuntu" with password "ubuntu". You'll use this user a few times, so set the credentials to something easy to remember
5. After installation, switch to root: sudo su
6. Change root's password to something easy to remember using ```passwd```
7. Generate keys: ```ssh-keygen```
8. Make the keys you just generated authorized: ```cp ~/.ssh/id_rsa.pub ~/.ssh/authorized_keys```
9. Edit the file /etc/ssh/sshd_config and change the line with "PermitRootLogin" so it reads PermitRootLogin yes
10. Restart SSH to activate the changes: service ssh restart
11. Run ifconfig and take note of the machine's IP
12. Open terminal on your host computer
13. Run (with your machine's IP substituted):
    ```ssh root@<your-machines-ip> 'cat ~/.ssh/id_rsa' > ~/.ssh/docker_test```
14. Run:
    ```ssh root@<your-machines-ip> 'cat ~/.ssh/id_rsa.pub' > ~/.ssh/docker_test.pub```
15. Run (back in the VM) ```shutdown now```
16. In VirtualBox, clone the template machine (check the checkbox to reinitialize MAC address). I named mine kube01
17. Start the new virtual machine and run echo 'kube01' > /etc/hostname and then reboot.
    Repeat 16 & 17 and name the machine kube02
18. Log in to each machine and run ```ifconfig``` to find out the IP addresses of the cloned machines.

The commands after this do not apply for this research.

## Install Kubernetes (k8s)

The web has an excellent article for installing k8s on Ubuntu 18.

[How to Install Kubernetes on Ubuntu 18](https://geekflare.com/install-kubernetes-on-ubuntu)


At this stage you will have two virtual machines (VM's).  **kube01** the master and **kube02** the slave.




 
WIP - More to come...




#### Last updated Tue 18 Feb 19:21:17 GMT 2020
