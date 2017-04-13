######
# See: https://hub.docker.com/_/php/
######

FROM python:3.6
MAINTAINER micooz <micooz@hotmail.com>

RUN apt-get update 
RUN apt-get install -y git vim
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
RUN apt-get install -y libssl-dev
RUN apt-get install -y libmagickwand-6.q16-dev --no-install-recommends \
&& ln -s /usr/lib/x86_64-linux-gnu/ImageMagick-6.8.9/bin-Q16/MagickWand-config /usr/bin

RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

ONBUILD COPY base_reqs.txt /usr/src/app/
ONBUILD RUN pip install -r base_reqs.txt 

ONBUILD COPY . /usr/src/app



