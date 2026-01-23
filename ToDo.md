# Inception

📋 Project Description
This project is about building a complete web infrastructure using Docker. I'll be creating a WordPress website with NGINX as a web server and MariaDB as the database, all running in separate Docker containers. The main goal is to understand containerization, orchestration with docker-compose, and system administration concepts.
Key Learning Outcomes:

Understanding Docker fundamentals (containers, images, volumes, networks)
Writing Dockerfiles from scratch
Orchestrating multi-container applications with docker-compose
Configuring web servers (NGINX with TLS/SSL)
Database management (MariaDB)
WordPress installation and configuration
Security practices (secrets management, environment variables)
System administration basics


✅ Complete To-Do List with Time Estimates
Phase 1: Environment Setup & Docker Basics ⏱️ Total: ~8 hours
Task 1.1: Set Up Virtual Machine

 Configure VM networking
 Take VM snapshot (backup point)

Task 1.2: Install Docker & Docker Compose

 Update system packages
 Install Docker Engine
 Install Docker Compose
 Add user to docker group (avoid sudo)
 Test with docker run hello-world
 Verify docker-compose installation
Estimated Time: 1 hour
Learning Focus: Package management, Docker installation

Task 1.3: Learn Docker Fundamentals

 Read Docker documentation (containers, images, volumes)
 Practice basic commands: docker run, docker ps, docker images
 Understand Dockerfile syntax (FROM, RUN, COPY, CMD, ENTRYPOINT)
 Learn about Docker volumes vs bind mounts
 Understand Docker networks
 Practice building a simple image
Estimated Time: 4-5 hours
Learning Focus: Docker core concepts
Resources:

Official Docker docs: https://docs.docker.com/get-started/
Docker tutorial videos


Phase 2: Project Structure & Configuration ⏱️ Total: ~3 hours

Task 2.2: Configure Domain & Hosts File

 Edit /etc/hosts file
 Add entry: 127.0.0.1 yourlogin.42.fr
 Test with ping yourlogin.42.fr
Estimated Time: 15 minutes
Learning Focus: DNS basics, hosts file

Task 2.3: Create Environment Files

 Define all environment variables (DOMAIN_NAME, MYSQL_USER, etc.)
 Add .env to .gitignore
 Document all variables needed
Estimated Time: 30 minutes
Learning Focus: Environment variables, security

Task 2.4: Set Up Secrets

 Create password files in secrets/ folder
 Generate strong passwords for DB root and user
 Create db_root_password.txt
 Create db_password.txt
 Create credentials.txt for WordPress users
 Add secrets/ to .gitignore
Estimated Time: 30 minutes
Learning Focus: Secrets management, security best practices

Task 2.5: Create Makefile

 Write basic Makefile structure
 Add all target (build and run)
 Add build target (docker-compose build)
 Add up target (docker-compose up)
 Add down target (stop containers)
 Add clean target (remove containers)
 Add fclean target (remove everything including volumes)
 Add re target (clean and rebuild)
Estimated Time: 1 hour
Learning Focus: Makefile syntax, automation


Phase 3: MariaDB Container ⏱️ Total: ~6 hours
Task 3.1: Learn MariaDB Basics

 Read about MariaDB vs MySQL
 Understand database initialization
 Learn about MariaDB configuration files
 Study user management and privileges
Estimated Time: 2 hours
Learning Focus: Database fundamentals

Task 3.2: Write MariaDB Dockerfile

 Choose base image (Alpine or Debian)
 Install MariaDB packages
 Copy configuration files
 Create initialization script
 Set up proper permissions
 Define ENTRYPOINT/CMD (no infinite loops!)
Estimated Time: 2 hours
Learning Focus: Dockerfile best practices, database setup

Task 3.3: Create MariaDB Configuration & Scripts

 Create custom my.cnf configuration file
 Write initialization script to:

Create database
Create users (admin + regular user)
Set passwords from secrets
Grant privileges


 Make script executable
 Test script logic
Estimated Time: 2 hours
Learning Focus: Bash scripting, SQL basics


Phase 4: WordPress + PHP-FPM Container ⏱️ Total: ~7 hours
Task 4.1: Learn WordPress & PHP-FPM

 Understand WordPress architecture
 Learn what PHP-FPM is and how it works
 Study WordPress configuration (wp-config.php)
 Learn about WordPress CLI (WP-CLI)
Estimated Time: 2 hours
Learning Focus: WordPress fundamentals, PHP-FPM

Task 4.2: Write WordPress Dockerfile

 Choose base image
 Install PHP-FPM and required extensions
 Install WordPress CLI
 Download WordPress core files
 Set up proper permissions
 Configure PHP-FPM to listen on port 9000
 Define ENTRYPOINT/CMD
Estimated Time: 3 hours
Learning Focus: PHP environment setup

Task 4.3: Create WordPress Setup Script

 Write script to:

Wait for MariaDB to be ready
Configure wp-config.php with env variables
Install WordPress via WP-CLI
Create admin user (no "admin" in username!)
Create regular user
Set site URL and title


 Test script thoroughly
Estimated Time: 2 hours
Learning Focus: WordPress automation, bash scripting


Phase 5: NGINX Container ⏱️ Total: ~8 hours
Task 5.1: Learn NGINX & SSL/TLS

 Understand NGINX as reverse proxy
 Learn NGINX configuration syntax
 Study SSL/TLS certificates
 Learn about TLSv1.2 and TLSv1.3
 Understand FastCGI and how NGINX talks to PHP-FPM
Estimated Time: 3 hours
Learning Focus: Web servers, HTTPS, reverse proxy

Task 5.2: Generate SSL Certificates

 Learn about self-signed certificates
 Generate SSL certificate and key using openssl
 Understand certificate fields (CN, etc.)
 Store certificates properly
Estimated Time: 1 hour
Learning Focus: SSL/TLS, cryptography basics

Task 5.3: Write NGINX Dockerfile

 Choose base image
 Install NGINX
 Copy SSL certificates
 Copy configuration files
 Expose port 443
 Define ENTRYPOINT/CMD
Estimated Time: 2 hours
Learning Focus: Web server containerization

Task 5.4: Configure NGINX

 Create nginx.conf file
 Configure server block:

Listen on port 443 (SSL)
Enable TLSv1.2 and TLSv1.3 only
Set up SSL certificates
Configure server name (yourlogin.42.fr)
Set root directory for WordPress
Configure FastCGI pass to WordPress container
Set up proper location blocks


 Test configuration syntax
Estimated Time: 2 hours
Learning Focus: NGINX configuration, FastCGI


Phase 6: Docker Compose Orchestration ⏱️ Total: ~5 hours
Task 6.1: Learn Docker Compose Basics

 Study docker-compose.yml syntax
 Understand services, networks, volumes
 Learn about depends_on
 Study restart policies
 Understand secrets in compose
Estimated Time: 2 hours
Learning Focus: Container orchestration

Task 6.2: Write docker-compose.yml

 Define version (3.8 or later)
 Create services section:

mariadb service
wordpress service
nginx service


 Configure each service:

Build context
Container name
Environment variables
Secrets
Networks
Volumes
Restart policy
Dependencies


 Define networks section (custom bridge network)
 Define volumes section (db volume, wordpress volume)
 Define secrets section
Estimated Time: 3 hours
Learning Focus: Multi-container applications


Phase 7: Testing & Debugging ⏱️ Total: ~8 hours
Task 7.1: Initial Build and Test

 Run make to build all containers
 Check for build errors
 Fix any Dockerfile issues
 Verify all images built successfully
Estimated Time: 2 hours
Learning Focus: Debugging, problem-solving

Task 7.2: Container Communication Testing

 Start containers with make up
 Check all containers are running: docker ps
 Test network connectivity between containers
 Verify MariaDB is accessible from WordPress
 Check logs: docker-compose logs
Estimated Time: 2 hours
Learning Focus: Docker networking, logging

Task 7.3: Service Verification

 Access https://yourlogin.42.fr in browser
 Verify SSL certificate (expect browser warning - it's self-signed)
 Check WordPress installation page loads
 Complete WordPress setup if needed
 Log in with admin user
 Log in with regular user
 Create a test post
Estimated Time: 2 hours
Learning Focus: Integration testing

Task 7.4: Volume & Persistence Testing

 Stop containers: make down
 Check volumes exist: docker volume ls
 Verify data in /home/yourlogin/data folder
 Restart containers
 Verify WordPress data persisted (posts still there)
 Verify database data persisted
Estimated Time: 1 hour
Learning Focus: Data persistence

Task 7.5: Security & Compliance Check

 Verify no passwords in Dockerfiles
 Check .env is in .gitignore
 Verify secrets folder is in .gitignore
 Confirm only port 443 is exposed
 Test TLS version (should only accept TLSv1.2/1.3)
 Verify no "latest" tags used
 Check admin username doesn't contain "admin"
 Confirm containers restart on crash
Estimated Time: 1 hour
Learning Focus: Security best practices


Phase 8: Documentation ⏱️ Total: ~6 hours
Task 8.1: Write README.md

 Add italicized first line with login(s)
 Write Description section (project goal, overview)
 Write Instructions section (how to compile, install, run)
 Write Resources section:

List documentation/tutorials used
Describe how AI was used (if applicable)


 Add Project Description section:

Explain Docker usage
Compare: VMs vs Docker
Compare: Secrets vs Environment Variables
Compare: Docker Network vs Host Network
Compare: Docker Volumes vs Bind Mounts


Estimated Time: 3 hours
Learning Focus: Technical writing, Docker concepts

Task 8.2: Write USER_DOC.md

 Explain what services are provided
 Document how to start the project
 Document how to stop the project
 Explain how to access website (https://yourlogin.42.fr)
 Explain how to access admin panel (/wp-admin)
 Document where credentials are stored
 Explain how to verify services are running
Estimated Time: 1.5 hours
Learning Focus: User documentation

Task 8.3: Write DEV_DOC.md

 List prerequisites (Docker, docker-compose, etc.)
 Explain environment setup from scratch
 Document configuration files and their purpose
 Explain secrets setup
 Document Makefile targets
 List useful Docker commands for management
 Explain where data is stored (volumes)
 Document how to access container shells for debugging
Estimated Time: 1.5 hours
Learning Focus: Developer documentation


Phase 9: Bonus (Optional) ⏱️ Total: ~10-15 hours
Task 9.1: Redis Cache

 Learn about Redis and caching
 Create Redis Dockerfile
 Configure WordPress to use Redis
 Add to docker-compose.yml
 Test cache functionality
Estimated Time: 3-4 hours

Task 9.2: FTP Server

 Learn about FTP/FTPS
 Choose FTP server (vsftpd recommended)
 Create FTP Dockerfile
 Configure to point to WordPress volume
 Add to docker-compose.yml
 Test file upload/download
Estimated Time: 3-4 hours

Task 9.3: Static Website

 Choose language (Python, Node.js, Go, etc.)
 Create simple static site
 Write Dockerfile
 Add to docker-compose.yml
 Configure NGINX to serve it
Estimated Time: 2-3 hours

Task 9.4: Adminer

 Learn about Adminer (database management tool)
 Create Adminer Dockerfile
 Add to docker-compose.yml
 Configure NGINX proxy for it
 Test database access
Estimated Time: 2 hours

Task 9.5: Service of Your Choice

 Choose useful service (Portainer, Grafana, etc.)
 Create Dockerfile
 Integrate with stack
 Prepare justification for defense
Estimated Time: 2-4 hours


🎯 Key Concepts to Master

Docker Fundamentals

Containers vs VMs
Images and layers
Volumes and data persistence
Networks and container communication


Dockerfile Best Practices

PID 1 and process management
No infinite loops (tail -f, sleep infinity)
Proper ENTRYPOINT vs CMD usage
Layer optimization


Web Stack Architecture

NGINX as reverse proxy
FastCGI protocol
SSL/TLS encryption
Database connections


Security

Secrets management
Environment variables
SSL certificates
User permissions


DevOps Practices

Infrastructure as Code
Container orchestration
Service dependencies
Health checks and restart policies


💡 Tips & Common Pitfalls
Tips:

Test each container individually before connecting them
Use docker logs <container> frequently for debugging
Keep Dockerfiles simple and readable
Comment your configuration files
Take VM snapshots before major changes

Common Pitfalls:

Using tail -f or infinite loops (FORBIDDEN!)
Hardcoding passwords in Dockerfiles
Using latest tag
Forgetting to expose/map ports correctly
Not waiting for database to be ready before WordPress starts
Wrong file permissions in containers


🔍 Validation Checklist
Before submission, verify:

 All containers build without errors
 All containers start and restart automatically
 Website accessible at https://yourlogin.42.fr
 SSL/TLS works (TLSv1.2 or TLSv1.3 only)
 WordPress has 2 users (admin + regular)
 Admin username doesn't contain "admin"
 Data persists after restart
 Volumes are in /home/yourlogin/data
 No passwords in Dockerfiles or Git
 .env and secrets in .gitignore
 README.md, USER_DOC.md, DEV_DOC.md complete
 Makefile works correctly
 No forbidden commands (tail -f, sleep infinity, etc.)
 Only port 443 exposed
 Custom docker network exists