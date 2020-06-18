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
Clone the repository locally by running: git clone https://github.com/colisee/booked.git
### Windows
Download [docker-desktop](https://www.docker.com/get-started) from the docker web site

## Running
- On Linux, open a terminal and run: docker-compose up
- On Windows,...

