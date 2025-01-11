# Install and Setup NGINX

## Prerequisites

1. Docker
2. Basics of Linux Commands
3. AWS Account

## Installation Steps

#### Starting Docker Container in Interactive Mode

1. Start the docker service in your device

2. Run an ubuntu based docker image in 'interactive mode' in the terminal, using -

    > docker run -it -p 8080:80 ubuntu

#### Installing NGINX in this docker container 

1. Update the packages, using -

    > apt-get update

    As we are using Linux based image, If we are using Ubuntu based image, we can use `sudo`

> **NOTE**: Use `uname` or `uname -a` to check the underlying OS

2. Install Nginx, using -

    > apt-get install nginx

3. Check Installation, using -
    
    > nginx -v

    OR 

    In the terminal, write -
    
    > nginx

    and then in the browser, goto `localhost:8080` (the port mapped to port 80, while spinning the docker container), there you will see the welcome page from Nginx

> **Note** : By default, Nginx runs on Port 80 (HTTP), here, we have mapped the port 8080 to the port 80, so we can access the Nginx using port 8080

#### Install vim

 Run the following command - 

    > apt-get install vim
