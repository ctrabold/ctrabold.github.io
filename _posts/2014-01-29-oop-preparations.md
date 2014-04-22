---
layout: post
title: "Continuous Delivery Workshop Preparations"
date: 2014-01-29 19:15
comments: false
tags:
  - workshops
  - howtos
---

## Overview

These instructions will guide you through an example project for the 'Continuous Delivery' workshop.

You will deploy the website through several stages:

    dev -> ci -> qa -> prod


## Requirements

To start the workshop right away we ask you to bring a laptop and prepare it as follows:

* Install VirtualBox: [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
* Install Vagrant [http://www.vagrantup.com/downloads.html](http://www.vagrantup.com/downloads.html)
* Ensure that you have *at least* 2.5GB of free space on your hard disk
* Ensure that your USB port is working so that we can provide the image via a portable Hard Drive/Stick.
* Make sure you don’t use local ports like `8181` and `8153`.
  We need these ports for accessing the apps on the VirtualMachine

## File structure of the example project

<pre>
.
├── README.md                     General instructions
├── Vagrantfile                   Config for starting the VM
├── app                           Example app for the workshop
└── vendor                        External files from vendors
    ├── Vagrant-1.4.3.dmg
    ├── Vagrant_1.4.3.msi
    ├── vagrant_1.4.3_i686.deb
    ├── vagrant_1.4.3_i686.rpm
    ├── vagrant_1.4.3_x86_64.deb
    ├── vagrant_1.4.3_x86_64.rpm
    ├── VirtualBox-4.3.2-90405-Win.exe
    ├── VirtualBox-4.3.2-90405-OSX.dmg
    └── ubuntu-12.04.2-amd64.box
</pre>


## How to use the example project

* Insert USB Stick
* Copy folder `cd_workshop` to local disk
* Eject the USB stick and pass it to the next student
* Install VirtualBox and Vagrant from `vendor` (if not installed already)
* Open the terminal and go to the folder on your local disk
* Run `vagrant up` on the terminal<br>
  Now the virtual machine starts up and consumes the local ports. It fetches the `.box` file from `./vendor` to create the VM
* Open [http://localhost:8153/](http://localhost:8153/) in your browser to see the CI-Server working
* Open [http://localhost:8181/](http://localhost:8181/) to see the umbrella page for our web project we will working on
<pre>
http://localhost:8181/workshop-dev  - Current status in `app`
http://localhost:8181/workshop-ci   - Stage after build
http://localhost:8181/workshop-qa   - Stage after tests
http://localhost:8181/workshop-prod - Production
</pre>
* SSH into the machine with `vagrant ssh`.<br>
  You should be able to run every command that is needed for the workshop as user `vagrant`.<br>
  You can use `sudo` without a password.
* In case you need the username and password:
<pre>
Username: vagrant
Password: vagrant
</pre>
* Go to the folder `/vagrant/app`, make changes and push them
<pre>
cd /vagrant/app

git add .
git commit -m "Update content"
git push origin master
</pre>
* See the CI-Server in action while fetching the changes and running the tests: [http://localhost:8153/view/CD-Pipeline/](http://localhost:8153/view/CD-Pipeline/)
* Improve the application and push the updates, when you are satisfied with your results.<br>
  You can edit the code directly on the host in your favourite editor / IDE.
* Approve the changes by starting the deployment to the next stage


## FAQ

F: Do I really need VirtualBox or may I use VMWare Workstation as well?<br>
A: We are using VirtualBox for our workshop. VMWare Workstation is currently not supported.
