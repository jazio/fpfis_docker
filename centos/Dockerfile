# ====================================================================================================
# This file contains all the commands a user could call on the command line to assemble an image.
# Based on this file and your OS context (local files PATH and URL) the command `docker build Dockerfile` will create a build.
# The build will be run by a component called docker daemon.

# Note: In order to effectively utilize the cache keep common instructions at the top of the Dockerfile and only add the alterations at the end.
# ====================================================================================================

FROM centos
MAINTAINER Ovi Farcas <farcaso@protonmail.com>


# Update the repository sources list once more
RUN yum clean all -y




RUN yum install -y \
	vim \
	git \
	tar \
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
	phpmyadmin \
	wget \

RUN a2enmod rewrite





