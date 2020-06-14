#
# Dockerfile: php-apache container
#
# Installation: build the container using docker-compose on the CLI
#

ARG  PHP_VERSION
FROM php:${PHP_VERSION:-7}-apache

# Enable the rewrite modules
RUN  a2enmod rewrite;

# retrieve additional php modules 
ARG  PHP_MOD
ADD  https://raw.githubusercontent.com/mlocati/docker-php-extension-installer/master/install-php-extensions /usr/local/bin/
RUN  chmod uga+x /usr/local/bin/install-php-extensions; \
     install-php-extensions ${PHP_MOD};

# Get the php project and set the proper ownership
COPY booked-2.7.8.zip ${PWD}
RUN  apt-get update && apt-get install -y unzip; \
     unzip ${PWD}/booked-2.7.8; \
     mv booked/* . && mv booked/.htaccess . && rmdir booked; \
     chown www-data:www-data * ; \
     apt-get purge -y unzip && apt-get autoremove -y;

# Set initial configuration
RUN  cp config/config.dist.php config/config.php; \
     sed -i config/config.php -e 's/127.0.0.1/booked-db/'; \
     sed -i config/config.php -e 's/bookedscheduler/booked/'; \
     sed -i config/config.php -e "s/\['registration.captcha.enabled'\] = 'true'/\['registration.captcha.enabled'\] = 'false'/"; \
     sed -i config/config.php -e "s/\['install.password'\] = ''/\['install.password'\] = 'B00k€d'/";

# Correct USER drop SQL statements
RUN  sed -i database_schema/create-user.sql -e 's/DROP USER/DROP USER IF EXISTS/'; \
     sed -i database_schema/full-install.sql -e 's/DROP USER/DROP USER IF EXISTS/';

