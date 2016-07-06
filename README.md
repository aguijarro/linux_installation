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
1) Change hostname

2) Modify hosts file

3) Create a new user named grader and grant this user sudo permissions.

4) Update all currently installed packages.

5) Configure the local timezone to UTC.

6) Change the SSH port from 22 to 2200

7) Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123), HTTPS, 5432 (Postgres)

8) Install and configure Apache to serve a Python mod_wsgi application

9) Install and configure PostgreSQL:
   * Do not allow remote connections
   * Create a new user named catalog that has limited permissions to your catalog application database

10) Install git, clone and set up Catalog App project.

11) Install virtualenv

12) Install Python requierements

Third-party resources you made use of to complete this project
--------------------------------------------------------------
http://www.binarytides.com/linux-commands-monitor-network/
https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands


Additional Functionality:
------------------------

1) Automatic Security Updates using GNOME Update Manager.

   * sudo apt-get install unattended-upgrades

   * sudo dpkg-reconfigure --priority=low unattended-upgrades	

2) Server monitoring

   * sudo apt-get install bwm-ng htop pastebinit whois

   * sudo apt-get install tcptrack

Configuration pg_hba.conf:
--------------------------

local   all             postgres                                peer
local   all             all                                     peer
host    all             all             127.0.0.1/32            md5
host    all             all             ::1/128                 md5
host    catalogdb       all             127.0.0.1/32            md5

Steps for configuration of users in Postgres:
--------------------------------------------

sudo -u postgres createuser -P -s -e catalogdb
CREATE DATABASE catalogdb WITH OWNER catalogdb;


Myapp.wsgi file:
---------------

import sys
import os

sys.path.insert(0, '/home/grader/fullstack-nanodegree-vm/vagrant/catalog')

activate_this = '/home/grader/fullstack-nanodegree-vm/vagrant/catalog/env/bin/activate_this.py'
execfile(activate_this, dict(__file__=activate_this))

if os.path.exists('.env'):
    print('Importing environment from .env...')
    for line in open('.env'):
        var = line.strip().split('=')
        if len(var) == 2:
            os.environ[var[0]] = var[1]

from app import app as application


* Add in app/__init__.py line
app = create_app('default')



