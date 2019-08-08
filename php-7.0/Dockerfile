FROM debian:9

# Update
RUN apt-get update

# Add php7.2 repository
RUN apt-get install -y apt-transport-https lsb-release ca-certificates wget
RUN wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
RUN echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list

# Update
RUN apt-get update

# Install php7.0 and apache2
RUN apt-get install -y curl \
	php7.0 \
	php7.0-common \
	php7.0-xdebug \
	php7.0-curl \
	php7.0-mbstring \
	php7.0-mysql \
	php7.0-dom \
	php7.0-ftp \
	php7.0-memcached \
	php7.0-fpm \
	php7.0-xml \
	php7.0-zip \
	php7.0-json \
	php7.0-intl \
	php7.0-gd \
	apache2 \
	libapache2-mod-php7.0

RUN echo "xdebug.remote_enable=on" >> /etc/php/7.0/cli/conf.d/20-xdebug.ini

# enable rewrite module
RUN a2enmod rewrite

# set env variables for site configuration
ENV SERVER_NAME www.example.com
ENV SERVER_ALIAS example.com
ENV DOCUMENT_ROOT /

COPY 000-default.conf /etc/apache2/sites-available/000-default.conf

EXPOSE 80
CMD apachectl -D FOREGROUND

