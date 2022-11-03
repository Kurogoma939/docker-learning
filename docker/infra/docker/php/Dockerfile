FROM php:7.3.1-fpm

RUN apt-get update \
  && apt-get install -y zip unzip libpng-dev libjpeg-dev libfreetype6-dev libzip-dev zlib1g-dev \
  && apt-get install -y libcurl4-openssl-dev pkg-config libssl-dev wget libpq-dev

RUN docker-php-ext-install -j$(nproc) pdo_mysql opcache gd mbstring opcache \
  && pecl install xdebug mongodb zip \
  && docker-php-ext-enable xdebug mongodb zip \
  && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
  && docker-php-ext-configure pgsql -with-pgsql=/usr/include/postgresql/ \
  && docker-php-ext-install pgsql pdo_pgsql

RUN apt-get install -y nano vim less

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

# nodejs
# RUN curl -sL https://deb.nodesource.com/setup_12.x | bash - \ 
#     && apt-get install -y nodejs \
#     && npm install npm@latest -g

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /apps/kurogoma/backend

# RUN npm install

RUN { \
  echo 'file_uploads = On'; \
  echo 'max_execution_time=-1'; \
  echo 'memory_limit=2000M'; \
  echo 'post_max_size=2000M'; \
  echo 'upload_max_filesize=2000M'; \
  } > /usr/local/etc/php/conf.d/uploads.ini