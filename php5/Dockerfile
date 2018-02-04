# Base imegs -> ubuntu:14.04
FROM ubuntu:14.04

# Block intaractive setting
ENV DEBIAN_FRONTEND noninteractive

# Update packages and Installation of various things needed
RUN apt-get -y update && apt-get -y upgrade && \
	apt-get -y install wget apache2 php5 php5-mysql php5-curl php5-intl php5-xmlrpc php5-gd
 
#	wget https://download.moodle.org/stable30/moodle-3.0.3.tgz -P /var/www && \
#	tar -xzvf /var/www/moodle-3.0.3.tgz -C /var/www/html --strip=1 --no-same-owner --no-same-permissions && \
#	rm /var/www/moodle-3.0.3.tgz

# Copy the configuration file
COPY ./moodle-php.ini /etc/php5/cli/php.ini
COPY ./moodle-apache2.conf /etc/apache2/apache2.conf

# Create directory for data and set permissions
RUN mkdir /var/www/moodledata && \
    chown -R www-data:www-data /var/www/moodledata

# Port setting
EXPOSE 80

# Cleanup, this is ran to reduce the resulting size of the image.
RUN apt-get clean autoclean && apt-get autoremove -y

# Launch apache2 on startup
CMD ["/usr/sbin/apachectl", "-D", "FOREGROUND"]
