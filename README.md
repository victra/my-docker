s# README #

This README would normally document whatever steps are necessary to get your application up and running.

### What is this repository for? ###

For laravel apps

### How do I get set up? ###

* install docker ---> https://docs.docker.com/docker-for-mac/install/#download-docker-for-mac
* install brew ---> https://www.howtogeek.com/211541/homebrew-for-os-x-easily-installs-desktop-apps-and-terminal-utilities
* install docker-compose via brew : $brew install docker-compose

### Preparation ###

* create .env file (there's sample in repo)  
* change value APP_ROOT with your current apps location  
* create server configuration for nginx under folder nginx/conf with format *.conf (there's sample under folder nginx)  
* for API apps there's special case, create folder api under your APP_ROOT path, and create index.php with standard echo (e.g <?php echo "THIS API" ?>)   
  under api folder. and clone all api repositories under api folder
  

### Startup ###

with current bash under directory docker-infrastructure run  
* $docker-compose up --build -d (run for first time or there's some change on docker files)  
* $docker-compose up -d name_service name_service e.g $docker-compose up -d web nginx php redis, that's if you want to not start all services  
* $docker-compose stop --> it's gonna stop all running container under current docker-compose directory it self  