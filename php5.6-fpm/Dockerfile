######
# See: https://hub.docker.com/_/php/
######

FROM php:5.6.30-fpm
MAINTAINER micooz <micooz@hotmail.com>

######
# You can install php extensions using docker-php-ext-install
######

RUN apt-get update 
RUN apt-get install -y git
RUN apt-get install -y libicu-dev icu-devtools
RUN apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libxslt1-dev \
        libmcrypt-dev \
        libpng12-dev 
RUN apt-get install -y libmcrypt-dev mysql-client 
RUN apt-get install -y apt-utils
RUN apt-get install -y libcurl4-openssl-dev
RUN docker-php-ext-install -j$(nproc) iconv mcrypt xsl intl zip pdo pdo_mysql mysql mysqli bcmath curl mbstring soap xml json iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-configure hash --with-mhash \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install -j$(nproc) hash
RUN apt-get install -y libssl-dev
RUN docker-php-ext-install -j$(nproc) openssl ; exit 0
RUN ls /usr/src/php/ext/openssl/ 
RUN cp /usr/src/php/ext/openssl/config0.m4 /usr/src/php/ext/openssl/config.m4
RUN docker-php-ext-install -j$(nproc) openssl 
#RUN curl -sS https://raw.githubusercontent.com/composer/getcomposer.org/master/web/installer | php && mv composer.phar /usr/local/bin/composer
RUN apt-get install -y libmagickwand-6.q16-dev --no-install-recommends \
&& ln -s /usr/lib/x86_64-linux-gnu/ImageMagick-6.8.9/bin-Q16/MagickWand-config /usr/bin \
&& pecl install imagick \
&& echo "extension=imagick.so" > /usr/local/etc/php/conf.d/ext-imagick.ini


#docker exec -it dockerlnmp_fpm_1 chown -R www-data:www-data /usr/share/ngnix/html
#docker exec -it dockerlnmp_fpm_1 /bin/bash
#docker exec -it dockerlnmp_fpm_1 /usr/local/bin/composer install

