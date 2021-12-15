# Docker

# Installation

Begin to Installation Docker on Ubuntu:

        Sudo -i: Enter the root authority
        
Then we use “apt” to update the package, we add the program and address of docker

        sudo apt-get update
        sudo apt-get install \
            ca-certificates \
            curl \
            gnupg \
            lsb-release
        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
        echo\"deb[arch=$(dpkg--print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
          $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
          
Then reflesh the list

        sudo apt-get update
        
So we could install the docker by sudo apt-get install docker-ce docker-ce-cli containerd.io

When I run this command, it said 12 packages have not been upgraded.
I use command sudo apt-get dist-upgrade to install the 12 packages

        apt-cache madison docker-ce
        
(To list that available versions, we need to install the special version of the Dockers Engine)

Install the special version of the Dockers Engine

        sudo apt-get install docker-ce=5:20.10.10~3-0~ubuntu-focal docker-ce-cli=5:20.10.10~3-0~ubuntu-focal containerd.io
        
To check if it is successful to install or not and if it is running or not
        
        sudo systemctl status docker

Still verify 

        sudo docker run hello-world
        
# Docker Compose

To install Docker compose

        sudo apt-get install docker-compose 

Set up a file called wo

        mkdir wo 
        
get into the file

        cd wo
        
Use command nano to set up the file ending in yml

        nano docker-compose.yml

We download Wordpress by the docker-compose.yml

        version: '3.3'
         services:
          db:
            image: mysql:5.7
          volumes:
            - db_data:/var/lib/mysql
          restart: always
          environment:
            MYSQL_ROOT_PASSWORD: root
            MYSQL_DATABASE: wordpress
            MYSQL_USER: wordpress
            MYSQL_PASSWORD: 12345678
          wordpress:
            depends_on:
              - db
          image: wordpress:latest
          ports:
            - "80:80"
          restart: always
          environment:
            WORDPRESS_DB_HOST: db
            WORDPRESS_DB_USER: wordpress
            WORDPRESS_DB_PASSWORD: 123456789
            WORDPRESS_DB_NAME: admin
          volume:
            db_data: {}
    
To run this file

        docker-compose up -d
        
Then we insert http:// localhost to get into WordPress

Here we get!


