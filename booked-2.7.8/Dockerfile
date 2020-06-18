#
# Dockerfile: php-apache container
#
# Installation: build the container using docker-compose on the CLI
#

ARG  PHP_VERSION

FROM php:${PHP_VERSION:-7}-apache

# Set the PHP.INI file & enable the rewrite modules
RUN  mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"; \
     a2enmod rewrite;

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
     chown -R www-data:www-data * ; \
     apt-get purge -y unzip && apt-get autoremove -y;

# Set initial configuration
ARG  INSTALLATION_PASSWORD
ARG  PWD_USR
RUN  cp config/config.dist.php config/config.php; \
     sed -i config/config.php -e 's/127.0.0.1/db/'; \
     sed -i config/config.php -e 's/bookedscheduler/booked/'; \
     sed -i config/config.php -e "s/\['registration.captcha.enabled'\] = 'true'/\['registration.captcha.enabled'\] = 'false'/"; \
     sed -i config/config.php -e "s/\['install.password'\] = ''/\['install.password'\] = '$INSTALLATION_PASSWORD'/"; \
     sed -i config/config.php -e "s/\['password'\] = 'password'/\['password'\] = '${PWD_USR}'/";

