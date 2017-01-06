#!/bin/bash

# [1] must install Docker-Compose was installed using the method below:
#--------------

curl -L "https://github.com/docker/compose/releases/download/1.9.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

chmod +x /usr/local/bin/docker-compose


## [2] Place vital docker and docker-compose files that one needs in this single project folder, i called the folder 'dpl' short for 'delivery pipe line' Files to check include 'Dockerfile, requirements.txt for python vm which is the 'web' services vm to install Django components. docker-compose.yml this is for docker compose to orchestrate the process and bring it all together. 

# [3] ececute command below,(whilst inside the folder):

 docker-compose run web django-admin.py startproject deliverypipeline .

# [NOTE] You will notice the creation of 'manage.py' and the 'deliverypipeline' folder that hosts more configuraiton files, the IP address 192.168.99.103 is for my own vm, you need to adjust to your own vm's/cloud resource requirement. The file is inside 'deliverypipelinefolder' called 'settings.py'. The line you will be after is ALLOWED_HOSTS = ['192.168.99.103:8000','192.168.99.1']. Put IPs relevant to your own environment.

# [4] (whilst inside the folder dpl) execute command docker-compose up. 

docker-compose up 

# [5] To make adjustment to a code you need to execute:  docker-compose build 

# [6] To view the Django display page you simply put the IP of the vm that contains the docker images. Remember the line [NOTE] where one must make IP adjustments. That vm or container may need adjustment in the file 'settings.py' depending on the resource or cloud one is using.

# [7] you will notice, (form the messages), that the two containers are:
# Stopping dpl_web_1 ...
# Stopping dpl_db_1 ...

