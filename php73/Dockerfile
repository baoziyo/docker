FROM ubuntu:18.04

RUN echo -e "deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse \ndeb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse \ndeb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse \ndeb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse \ndeb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse \ndeb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse \ndeb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse \ndeb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse \ndeb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse \ndeb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse" > /etc/apt/sources.list \
  && apt-get update && apt-get install -y software-properties-common tzdata zip curl gcc git make autoconf libc-dev pkg-config libmcrypt-dev \
  && LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php \
  && apt-get update && apt-get install -y php7.3-dev php7.3-cli php7.3-curl php7.3-intl php7.3-mysql php7.3-gd php7.3-zip php7.3-intl php7.3-gd php7.3-xml php7.3-phpdbg php7.3-bcmath php7.3-mbstring php-pear

RUN pecl channel-update pecl.php.net \
  && pecl install redis \
  && echo "extension=redis.so" > /etc/php/7.3/mods-available/redis.ini \
  && cd /etc/php/7.3/cli/conf.d && ln -s ../../mods-available/redis.ini 30-redis.ini \
  && cd /etc/php/7.3/phpdbg/conf.d && ln -s ../../mods-available/redis.ini 30-redis.ini \
  && pecl install swoole \
  && echo "extension=swoole.so" > /etc/php/7.3/mods-available/swoole.ini \
  && cd /etc/php/7.3/cli/conf.d && ln -s ../../mods-available/swoole.ini 30-swoole.ini \
  && cd /etc/php/7.3/phpdbg/conf.d && ln -s ../../mods-available/swoole.ini 30-swoole.ini 