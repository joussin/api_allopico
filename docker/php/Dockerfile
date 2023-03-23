FROM php:8.0.12-fpm

# Arguments defined in docker-compose.yml
ARG user
ARG uid


#ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/
#
#RUN apt-get update && apt-get install -y \
#    build-base \
#    freetype-dev \
#    libjpeg-turbo-dev \
#    libpng-dev \
#    libzip-dev \
#    zip \
#    jpegoptim optipng pngquant gifsicle \
#    vim \
#    unzip \
#    git \
#    oniguruma-dev \
#    curl
#
#RUN docker-php-ext-install pdo_mysql mbstring zip exif pcntl
##RUN docker-php-ext-configure gd --with-gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-png-dir=/usr/include/
#RUN docker-php-ext-configure gd
#RUN docker-php-ext-install gd





# Install system dependencies
RUN apt-get update && apt-get install -y \
    git \
    zip \
    curl \
    sudo \
    unzip \
    libicu-dev \
    libbz2-dev \
    libpng-dev \
    libjpeg-dev \
    libzip-dev \
    libmcrypt-dev \
    libreadline-dev \
    libxml2-dev \
    libfreetype6-dev \
    apt-file \
    wget \
    nano \
    g++

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install PHP extensions
RUN docker-php-ext-install pdo_mysql

#RUN docker-php-ext-install \
#    gd \
#    bz2 \
#    intl \
#    soap  \
#    iconv  \
#    bcmath  \
#    opcache  \
#    calendar  \
#    mbstring   \
#    pdo_mysql   \
#    pcntl        \
#    zip

# Get latest Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Create system user to run Composer and Artisan Commands
RUN id
RUN groupadd -g "${uid}" ${user} \
    && useradd --create-home --no-log-init -u "${uid}" -g ${user} -G sudo,www-data,root ${user}
#RUN useradd -G sudo,www-data,$user,root -u $uid -d /home/$user $user
#RUN mkdir -p /home/$user/.composer && \
#    chown -R $user:$user /home/$user
#RUN addgroup -g 1000 -S www && \
#    adduser -u 1000 -S www -G www

# Set the user
USER $user
RUN id

# Everything after this point will run as $user user with a specific UID/GID

# php version
RUN php -v

# php modules
RUN php -m

WORKDIR /var/www/html/

EXPOSE 9000
