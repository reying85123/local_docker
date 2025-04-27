FROM php:7.4-fpm

ENV TZ=Asia/Taipei

RUN apt-get update && apt-get install -y \
    zip unzip git curl nano supervisor wget \
    libpng-dev libjpeg62-turbo-dev libfreetype6-dev libonig-dev \
    libxml2-dev libzip-dev libpq-dev libxslt-dev \
    libssl-dev libcurl4-openssl-dev pkg-config \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install \
        pdo \
        pdo_mysql \
        gd \
        mbstring \
        xml \
        zip \
        bcmath \
        pcntl \
        opcache \
        xsl \
        sockets \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN pecl install redis && docker-php-ext-enable redis || echo "redis install failed"
RUN pecl install swoole && docker-php-ext-enable swoole || echo "swoole install failed"

RUN apt-get update && apt-get install -y wget fontconfig && \
    wget https://github.com/wkhtmltopdf/packaging/releases/download/0.12.6-1/wkhtmltox_0.12.6-1.stretch_amd64.deb -O wkhtmltox.deb && \
    dpkg -i wkhtmltox.deb || apt-get install -f -y && \
    rm wkhtmltox.deb

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

CMD ["php-fpm"]
