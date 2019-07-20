FROM php:7.2-fpm

# Install required librairies
RUN apt-get update && apt-get install -y \
    git \
    unzip \
    zlib1g-dev \
    libjpeg-dev\
    libpng-dev\
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpq-dev \
    libicu-dev g++ \
    libcurl4-openssl-dev \
    libxml2-dev \
    htop \
    libfreetype6-dev \
    mysql-client

RUN apt-get -y --no-install-recommends install curl ca-certificates unzip \
        php7.2-cli php7.2-curl php-apcu php-apcu-bc \
        php7.2-json php7.2-mbstring php7.2-opcache php7.2-readline php7.2-xml php7.2-zip \
# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer --version

# Configure PHP extensions
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

# Install PHP extensions
RUN docker-php-ext-install pdo pdo_mysql zip gd intl

# Let's clean all the junk
RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/* ~/.composer

# Import custom php.ini
COPY ./php.ini /usr/local/etc/php/

WORKDIR /var/www
