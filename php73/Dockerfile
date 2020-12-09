FROM ubuntu:18.04

RUN apt-get update && apt-get install -y software-properties-common \
  && LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php \
  && apt-get update && apt-get install -y \
  php7.3-dev \
  php7.3-cli \
  php7.3-curl \
  php7.3-intl \
  php7.3-mysql \
  php7.3-gd \
  php7.3-zip \
  php7.3-json \
  php7.3-gd \
  php7.3-xml \
  php7.3-phpdbg \
  php7.3-bcmath \
  php7.3-mbstring \
  php7.3-pgsql \
  php7.3-sqlite \
  php7.3-sqlite3 \
  php7.3-memcached \
  php-pear \
  libcurl4-openssl-dev \
  libedit-dev \
  libssl-dev \
  libxml2-dev \
  xz-utils \
  libsqlite3-dev \
  rsync \
  sqlite3 \
  git \
  curl \
  vim \
  nano \
  postgresql-client

RUN pecl channel-update pecl.php.net \
  && pecl install redis \
  && echo "extension=redis.so" > /etc/php/7.3/mods-available/redis.ini \
  && cd /etc/php/7.3/cli/conf.d && ln -s ../../mods-available/redis.ini 30-redis.ini \
  && cd /etc/php/7.3/phpdbg/conf.d && ln -s ../../mods-available/redis.ini 30-redis.ini \
  && pecl install swoole \
  && echo "extension=swoole.so" > /etc/php/7.3/mods-available/swoole.ini \
  && cd /etc/php/7.3/cli/conf.d && ln -s ../../mods-available/swoole.ini 30-swoole.ini \
  && cd /etc/php/7.3/phpdbg/conf.d && ln -s ../../mods-available/swoole.ini 30-swoole.ini 

RUN curl -s http://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer