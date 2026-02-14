# Inception

_This project has been created as part of the 42 curriculum by nfakih._

# Description

## Dockerfile
    - Base OS
        - Debian has better php support and is easier to work with
    - Install PHP and extensions
        - So php can talk to the database
    - Copy config files
    - Command to run setup script
# Instructions


# Docker
From: specifies the base image, and we add on top
Run: to execute a command in the terminal of the container
cmd: to specify the default command that shold be run when a container is started from the image
services: used to define the services that the application consists of
volume: used to define presistent storage
docker compose: multi container application
nginx: handles server side requests for web applications, and can be configured to handle ssl
TLS: transport layer security. used to establish secure communication between two parties over the internet. works by using public key encryption, the client and server exchange a series of messages to establish this connection, including the exchange of digital certificates and negotiation of encyrption keys.
# ssl
-x509 creates a self signed certificate
-nodes dont encrypt with private key with a password
-days expiration\20148 size in bits
-keyout /etc/nginx/ssl/nginx.key where to save the private key
-out /etc/nginx/ssl/nginx.crt certificate

# nginx
How NGINX works with WordPress:
User → NGINX (port 443) → PHP-FPM (port 9000) → MariaDB (port 3306)

User requests https://nfakih.42.fr/index.php
NGINX receives request on port 443
NGINX sees it's a .php file
NGINX asks PHP-FPM "Hey, process this PHP file for me"
PHP-FPM runs the PHP code (which might query MariaDB)
PHP-FPM sends the result back to NGINX
NGINX sends the result to the user

nginx.conf tells NGINX how to do steps 2, 3, 4, 6, and 7!

User requests: https://nfakih.42.fr/index.php
                    ↓
            NGINX receives on port 443
                    ↓
    Matches location ~ \.php$ (it's a .php file!)
                    ↓
    fastcgi_pass wordpress:9000
    (Send to WordPress container on port 9000)
                    ↓
            PHP-FPM receives request
                    ↓
    Executes /var/www/html/index.php
                    ↓
    Returns HTML result to NGINX
                    ↓
        NGINX sends result to user

# Resources

Learning docker: 
https://www.youtube.com/watch?v=gAkwW2tuIqE 
https://github.com/Forstman1/inception-42
https://www.youtube.com/watch?v=pg19Z8LL06w
# AI Usage