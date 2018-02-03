# Base imegs -> ubuntu:14.04
FROM ubuntu:14.04

# Block intaractive setting
ENV DEBIAN_FRONTEND noninteractive

# Set ENV Variables externally Moodle_URL should be overridden.
# ENV MOODLE_URL http://127.0.0.1
# ENV MYSQL_HOST mdldb

# Update packages
RUN apt-get -y update && apt-get -y upgrade
# Installation of various things needed
RUN apt-get -y install apache2 php5 php5-mysql php5-curl php5-intl php5-xmlrpc php5-gd

# Copy the configuration file
COPY ./moodle-php.ini /etc/php5/cli/php.ini
COPY ./moodle-apache2.conf /etc/apache2/apache2.conf

# Create directory for data and set permissions
RUN mkdir /var/www/moodledata
RUN chown -R www-data:www-data /var/www/moodledata


# Port setting
EXPOSE 80

# Cleanup, this is ran to reduce the resulting size of the image.
RUN apt-get clean autoclean && apt-get autoremove -y
#  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /var/lib/dpkg/* /var/lib/cache/* /var/lib/log/*

# Launch apache2 on startup
CMD ["/usr/sbin/apachectl", "-D", "FOREGROUND"]
