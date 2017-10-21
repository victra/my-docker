FROM ubuntu:16.04

MAINTAINER kusuma.asdani@bizzy.co.id

RUN DEBIAN_FRONTEND=noninteractive apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y software-properties-common && \
    DEBIAN_FRONTEND=noninteractive LC_ALL=C.UTF-8 add-apt-repository -y ppa:ondrej/php && \
    DEBIAN_FRONTEND=noninteractive apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --force-yes git && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --force-yes \
    php7.1 \
    php7.1-bcmath \
    php7.1-cgi \
    php7.1-cli \
    php7.1-common \
    php7.1-curl \
    php7.1-dev \
    php7.1-fpm \
    php7.1-gd \
    php7.1-intl \
    php7.1-json \
    php7.1-mbstring \
    php7.1-mcrypt \
    php7.1-opcache \
    php7.1-readline \
    php7.1-soap \
    php7.1-xml \
    php7.1-zip && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --force-yes python-software-properties && \
    curl -sL https://deb.nodesource.com/setup_6.x | bash - && \
    DEBIAN_FRONTEND=noninteractive apt-get -y --force-yes install nodejs && \
    npm install -g npm@4.6.1 gulp@3.9.1 && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y libssl-dev openssl pkg-config libsslcommon2 libsslcommon2-dev && \
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    pecl install mongodb && \
    echo 'extension=mongodb.so' > /etc/php/7.1/cli/conf.d/20-mongodb.ini && \
    echo 'extension=mongodb.so' > /etc/php/7.1/fpm/conf.d/20-mongodb.ini

RUN mkdir -p /www/bizzy/public_html/apps && mkdir /root/.ssh

COPY files/php-fpm.conf /etc/php/7.1/fpm/php-fpm.conf
COPY files/www.conf /etc/php/7.1/fpm/pool.d/www.conf
COPY files/php.ini /etc/php/7.1/fpm/php.ini
COPY rsa/id_rsa /root/.ssh/id_r:sa
COPY rsa/id_rsa.pub /root/.ssh/id_rsa.pub

RUN chmod 600 /root/.ssh/id_rsa*

EXPOSE 9000

CMD ["/usr/sbin/php-fpm7.1", "--nodaemonize"]