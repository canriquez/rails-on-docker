## Introduction

This repository provides a multi-container setup for a Rails backend, along with Sidekiq, Redis, PostgreSQL, and an Nginx reverse proxy. Docker Compose is used to manage the services and provide a local development environment.

## Contents
The repository contains the following components:

`docker-compose.yml`: Defines the application services, volumes, and network configuration.
`Dockerfile`: Builds the Rails backend custom Docker image.
`Dockerfile.nginx`: Builds the Nginx custom Docker image.
`reverse-proxy.conf`: Contains the reverse proxy configuration for Nginx.
`server/rails-backend`: The Rails application directory.
`.env`: An example environment file for setting up environment variables.

## Built With

- Ruby 3.0.3
- Ruby on Rails 7.0.4.2
- sidekiq
- RSpec
- Capybara
- FactoryBot
- Shoulda-Matchers


### Requirements 📋
```
- Docker Core / Docker composer/ Rancher installed in the system
- Git
```
### Instalation 🔧
```
* Clone the repository 
* In the root of the project run:

sudo docker-compose up 

* After the first run, A DB error will show in the console. Hit Ctr-C and run migrations:

sudo docker-compose run rails-backend rake db:create
sudo docker-compose run rails-backend rake db:migrate

* After migration, run the compose again:

sudo docker-compose up 

* Nginx reverse proxy server will run on port 80

```
## Environment set up requirements

Create a .env file in the root to build the environment variables for docker build.

```
USER_ID=1000
GROUP_ID=1000
SECRET_TOKEN=Wa4KduthisismysecretUuc7jBVFwuwn
WORKER_PROCESSES=1
LISTEN_ON=0.0.0.0:8010
DATABASE_URL=postgresql://rails-backend:test_db_password@postgres:5432/rails-backend?encoding=utf8&pool=5&timeout=5000
CACHE_URL=redis://redis:6379/0
JOB_WORKER_URL=redis://redis:6379/0
```

## Stop the application:

Press Ctrl+C in the terminal where you ran docker-compose up, or run the following command in another terminal:

<pre>
&#96;&#96;&#96;bash
docker-compose down
&#96;&#96;&#96;
</pre>

This command stops and removes the containers, networks, and volumes defined in the docker-compose.yml file.

## Author ✒️
* **Carlos Rafael Anriquez** - *Initial Work* - [Carlos Anriquez](https://github.com/canriquez)

