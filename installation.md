---
title: Installation
lang: en-US
---

# Installation

- [Manual Installation](#manual-installation)
- [Docker Installation](#docker-installation)
- [Digital Ocean (Docker)](#digital-ocean-docker)

## Manual Installation

### Requirements

```
PHP >= 7.4.0
BCMath PHP Extension
Ctype PHP Extension
JSON PHP Extension
Mbstring PHP Extension
OpenSSL PHP Extension
PDO PHP Extension
Tokenizer PHP Extension
XML PHP Extension
```

### Step 1 : Download

[Download](http://craterapp.com/downloads) the latest Crater package.

Alternatively, If you are a developer, follow the installation steps for your project on [this Link](./developer-guide.md)

### Step 2 : Upload to Server

Upload the downloaded zip file to your Server and unzip it, you should see the Crater folder.

### Step 3 : Point the domain to the uploaded folder

Point your domain or subdomain to the `public` directory inside the Crater folder.

Please note that, Crater must be installed on a primary domain or subdomain. Installing on a sub-folder will not work, for example:

- `example.com/craterapp` (Invalid)
- `localhost/crater` (Invalid)
- `example.com` (Valid)
- `crater.example.com` (Valid)
- `crater.test` (Valid)

### Step 3: Fix File Permissions

In your crater root folder, run command: `chmod -R 775 ./`

### Step 4 : Complete installation wizard

Open the link to the domain in the browser (Example: `https://demo.craterapp.com`) and complete the installation wizard as directed.

## Docker Installation

### Step 1 : Install Docker

Install Docker on your host: [https://docs.docker.com/install/](https://docs.docker.com/install/)

### Step 2 : Install Docker Compose

Install docker-compose by using this guide: [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)

### Step 3 : Clone repository

Clone the repository by running this command: `git clone https://github.com/crater-invoice/crater`

### Step 4 : Run below commands

Change your current working directory and run your app using below commands:

```
$ cd crater
$ cp .env.example .env
$ docker-compose up -d
$ ./docker-compose/setup.sh
```

### Step 5 : Complete installation wizard

Open your web browser and go to your given domain (default: [http://localhost](http://localhost)) and follow the installation wizard.

On Installation wizard - Database setup, use below credentials:

- Database Host: `db`
- Database Name: `crater`
- Database Username: `crater`
- Database Password: `crater`

## Digital Ocean (Docker)

### Prerequisites

- Access to an Ubuntu 18.04 local machine or development server as a non-root user with sudo privileges. If you’re using a remote server, it’s advisable to have an active firewall installed. To set these up, please refer to [Initial Server Setup Guide for Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-18-04) on Digital Ocean.

- Docker installed on your server, following Steps 1 and 2 of [How To Install and Use Docker on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04).

- Docker Compose must installed on your server. You can refer to this Guide: [How To Install Docker Compose on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-18-04).

### Installation

#### Step 1 : Clone repository

Clone the repository by running these commands:

```
cd ~
git clone https://github.com/crater-invoice/crater
```

#### Step 2: Verify Permissions 

Please verify that your current user's UID matches with given UID on [docker-compose.yml](https://github.com/crater-invoice/crater/blob/master/docker-compose.yml#L8) file in the application's root folder:

````
    build:
      args:
        user: crater-user
        uid: 1000
````

If it doesn't match, Update the compose.yml file before going ahead with step 3.

Hint: You can get the UID by running `id` command in the terminal (Note: If you don't do this step correctly, then you may get an error on step 4).

#### Step 3 : Setup docker containers

Change your current working directory and start containers using the given commands below:

```
$ cd crater
$ cp .env.example .env
$ docker-compose up -d
```

#### Step 4 : Install composer depencies & generate app key

Now wait for a few minutes until the containers are built and started. After that run the below script command to install composer dependencies & generate unique application key:

```
$ ./docker-compose/setup.sh
```

#### Step 5 : Complete installation wizard

Open your web browser and go to your given domain and follow the installation wizard.

On Installation wizard - Database setup, use below credentials:

- Database Host: `db`
- Database Name: `crater`
- Database Username: `crater`
- Database Password: `crater`
