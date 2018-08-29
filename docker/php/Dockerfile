FROM php:7.1-fpm

RUN apt-get update && apt-get install -y \
  curl \
  wget \
  git \
  vim \
  libfreetype6-dev \
  libjpeg62-turbo-dev \
  libxslt-dev \
  libicu-dev \
  libmcrypt-dev \
  libpng-dev \
  libxml2-dev \
  libpq-dev \
  libxpm-dev \
  libvpx-dev \
  xclip \
  gnupg \
  zip \
  unzip \
  && pecl install xdebug \
  && docker-php-ext-enable xdebug \
  && docker-php-ext-install -j$(nproc) mcrypt \
  && docker-php-ext-install -j$(nproc) mbstring \
  && docker-php-ext-install -j$(nproc) gd \
  && docker-php-ext-install -j$(nproc) intl \
  && docker-php-ext-install -j$(nproc) iconv \
  && docker-php-ext-install -j$(nproc) zip \
  && docker-php-ext-install -j$(nproc) mysqli \
  && docker-php-ext-install -j$(nproc) pdo_mysql \
  && docker-php-ext-install -j$(nproc) exif \
  && docker-php-ext-configure gd \
  --with-freetype-dir=/usr/include/ \
  --with-jpeg-dir=/usr/include/ \
  --with-xpm-dir=/usr/lib/x86_64-linux-gnu/ \
  --with-vpx-dir=/usr/lib/x86_64-linux-gnu/

RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer

CMD ["php-fpm"]
