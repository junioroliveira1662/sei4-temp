# Imagem base
FROM php:7.3.12

# Instalação das dependências do SEI
RUN apt-get update && \
    apt-get install -y libbz2-dev libxml2-dev libgd-dev libcurl4-openssl-dev libexif-dev libssl-dev libicu-dev libpq-dev libmemcached-dev wget unzip && \
    docker-php-ext-install bz2 calendar exif fileinfo gd gettext mysqli opcache pdo pdo_mysql soap sodium zip && \
    pecl install memcached && \
    docker-php-ext-enable memcached

# Instalação do wkhtmltopdf
RUN apt-get install -y wkhtmltopdf xvfb

# Instalação do Java Runtime
RUN apt-get install -y default-jre

# Instalação do ffmpeg
RUN apt-get install -y ffmpeg

# Configuração do Apache
RUN a2enmod rewrite && \
    echo "ServerName localhost" >> /etc/apache2/apache2.conf

# Configuração do PHP
RUN echo "upload_max_filesize = 50M" > /usr/local/etc/php/conf.d/upload_max_filesize.ini && \
    echo "post_max_size = 50M" > /usr/local/etc/php/conf.d/post_max_size.ini && \
    echo "extension=uploadprogress.so" > /usr/local/etc/php/conf.d/uploadprogress.ini && \
    echo "extension=oci8.so" > /usr/local/etc/php/conf.d/oci8.ini && \
    echo "date.timezone = America/Sao_Paulo" > /usr/local/etc/php/conf.d/timezone.ini

# Copiação dos arquivos do SEI
# COPY sei /var/www/html
# COPY config /opt/sei/config

# Permissões
# RUN chown -R www-data:www-data /var/www/html /opt/sei/config && \
#     chmod -R 770 /var/www/html /opt/sei/config && \
#     chmod +x /opt/sei/config/wkhtmltopdf-amd64

# Abertura da porta 80
EXPOSE 80
