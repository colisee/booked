This project is my personal attempt (as well as self-learning) to containerize the open-source [booked](https://www.bookedscheduler.com/) application, using [docker](https://www.docker.com/).
2 services (ie. containers) are made available:
+ web (a container with Apache and php with the mysqli module)
+ db (a container with MySQL)

## Table of content
- [Installation](#installation)
    - [Linux](#linux)
    - [Windows](#windows)
- [Running](#running)

## INSTALLATION
### Linux
Ensure that you installed the necessary packages:
- git (to clone this repository to your PC)
- docker.io
Clone this repository locally by running: git clone https://github.com/colisee/booked.git
### Windows
Ensure that you download & install the necessary software:
- [docker-desktop](https://www.docker.com/get-started)
- [git for Windows](https://gitforwindows.org/)
Clone this repository locally by running GIT and indicating https://github.com/colisee/booked.git
## Running
- On either OS, open a terminal, switch to the directory where you cloned the repository, open the file ".env" and take a note of the default values (you will need them in a few seconds). Optionally, you can change them
- Run: docker-compose up and wait until the Mysql container (called booked-db) is ready
- Open your web browser and go to "http://localhost/Web/install"
- Enter the value of "INSTALLATION_PASSWORD" on the 1st screen
- Enter "root" on the 1st field of the 2nd screen and the vaue of "MYSQL_ROOT_PASSWORD" on the 2nd field of the 2nd screen
- Select "Create database" only and validate
- Once the database is created (ignore the error messages) go to "http://localhost/Web"
- Click on register and create the first user (it will be the admin)
- Setup the application and enjoy!

