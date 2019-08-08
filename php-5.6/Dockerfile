FROM debian:9

# Update
RUN apt-get update

# Add php7.2 repository
RUN apt-get install -y apt-transport-https lsb-release ca-certificates wget
RUN wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
RUN echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list

# Update
RUN apt-get update

# Install php5.6 and apache2
RUN apt-get install -y curl \
	php5.6 \
	php5.6-common \
	php5.6-xdebug \
	php5.6-curl \
	php5.6-mbstring \
	php5.6-mysql \
	php5.6-dom \
	php5.6-ftp \
	php5.6-memcached \
	php5.6-fpm \
	php5.6-xml \
	php5.6-zip \
	php5.6-json \
	php5.6-intl \
	php5.6-gd \
	apache2 \
	libapache2-mod-php5.6

RUN echo "xdebug.remote_enable=on" >> /etc/php/5.6/cli/conf.d/20-xdebug.ini

# enable rewrite module
RUN a2enmod rewrite

# set env variables for site configuration
ENV SERVER_NAME www.example.com
ENV SERVER_ALIAS example.com
ENV DOCUMENT_ROOT /

COPY 000-default.conf /etc/apache2/sites-available/000-default.conf

EXPOSE 80
CMD apachectl -D FOREGROUND

