# ====================================================================================================
# This file contains all the commands a user could call on the command line to assemble an image.
# Based on this file and your OS context (local files PATH and URL) the command `docker build Dockerfile` will create a build.
# The build will be run by a component called docker daemon.
# ====================================================================================================

# Pulling repository docker.io/library/debian.
FROM debian:jessie

MAINTAINER Ovi Farcas <farcaso@protonmail.com>
ENV DEBIAN_FRONTEND noninteractive

# Install packages.
RUN apt-get update
RUN apt-get install -y \
	vim \
	git \
	apache2 \
	php5-cli \
	php5-mysql \
	php5-gd \
	php5-curl \
	php5-xdebug \
	php5-sqlite \
	libapache2-mod-php5 \
	curl \
	mysql-server \
	mysql-client \
	openssh-server \
	phpmyadmin \
	wget \
	unzip \
	cron \
	supervisor
RUN apt-get clean

# ====================================================================================================
# Configure Apache.
# ====================================================================================================
RUN sed -i 's/AllowOverride None/AllowOverride All/' /etc/apache2/apache2.conf
RUN sed -i 's/DocumentRoot \/var\/www\/html/DocumentRoot \/var\/www/' /etc/apache2/sites-available/000-default.conf
RUN sed -i 's/DocumentRoot \/var\/www\/html/DocumentRoot \/var\/www/' /etc/apache2/sites-available/default-ssl.conf
RUN echo "Listen 8080" >> /etc/apache2/ports.conf
RUN echo "Listen 8081" >> /etc/apache2/ports.conf
RUN echo "Listen 8443" >> /etc/apache2/ports.conf
RUN sed -i 's/VirtualHost \*:80/VirtualHost \*:\*/' /etc/apache2/sites-available/000-default.conf
RUN sed -i 's/VirtualHost __default__:443/VirtualHost _default_:443 _default_:8443/' /etc/apache2/sites-available/default-ssl.conf
RUN a2enmod rewrite
# todo enable SSL



# ====================================================================================================
# Configure PHP.
# ====================================================================================================
# Make errors visible.
RUN sed -i 's/display_errors = Off/display_errors = On/' /etc/php5/apache2/php.ini
RUN sed -i 's/display_errors = Off/display_errors = On/' /etc/php5/cli/php.ini
# Setup XDebug.
RUN echo "xdebug.max_nesting_level = 300" >> /etc/php5/apache2/conf.d/20-xdebug.ini
RUN echo "xdebug.max_nesting_level = 300" >> /etc/php5/cli/conf.d/20-xdebug.ini

# ====================================================================================================
# @todo Configure Blackfire.
# ====================================================================================================
# ====================================================================================================
# @todo Configure PHPMyAdmin.
# ====================================================================================================

# ====================================================================================================
# @todo Configure SSH.
# ====================================================================================================
# ====================================================================================================
# @todo Configure PHPMyAdmin.
# ====================================================================================================
# Setup MySQL, bind on all addresses.
RUN sed -i -e 's/^bind-address\s*=\s*127.0.0.1/#bind-address = 127.0.0.1/' /etc/mysql/my.cnf


# ====================================================================================================
# @todo Download // Install // Configure starterkit.
# ====================================================================================================

RUN /etc/init.d/mysql start && cd /var/www 

EXPOSE 80 3306 22 443