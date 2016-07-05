Linux Server Configuration
==========================

description
-----------

In this project you will be deploying the web application that you developed earlier for Project 3: Item Catalog. Udacity and Amazon have provided a virtual server in Amazon's Elastic Compute Cloud (EC2) for you to use for this project. When you complete the project your application will be accessible to the public!

Public IP address: 
-----------------
52.38.67.31

SSH Port:
--------
2200

Web application Url:
-------------------
http://ec2-52-38-67-31.us-west-2.compute.amazonaws.com/

A summary of software you installed and configuration changes made:
------------------------------------------------------------------
Change hostname
Modify hosts file
Create a new user named grader and grant this user sudo permissions.
Update all currently installed packages.
Configure the local timezone to UTC.
Change the SSH port from 22 to 2200
Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123)
Install and configure Apache to serve a Python mod_wsgi application
Install and configure PostgreSQL:
   Do not allow remote connections
   Create a new user named catalog that has limited permissions to your catalog application database
Install git, clone and set up Catalog App project.
Install virtualenv
Install Python requierements

Third-party resources you made use of to complete this project
--------------------------------------------------------------
http://www.binarytides.com/linux-commands-monitor-network/


Additional Functionality:
------------------------

Automatic Security Updates using GNOME Update Manager.
   sudo apt-get install unattended-upgrades
   sudo dpkg-reconfigure --priority=low unattended-upgrades	

Server monitoring
   sudo apt-get install bwm-ng htop pastebinit whois
   sudo apt-get install tcptrack

