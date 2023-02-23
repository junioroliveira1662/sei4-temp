
FROM image-registry.openshift-image-registry.svc:5000/openshift/php:latest

# Copie o seu código fonte para o diretório de trabalho
COPY . /app

# Defina o diretório de trabalho
WORKDIR /app

# Instale as dependências do PHP
# RUN apt-get update && \
#     apt-get install -y \
#         libpq-dev \
#         libzip-dev && \
#     docker-php-ext-install pdo pdo_pgsql zip

# Exponha a porta 80
EXPOSE 80

# Inicie o servidor da web do PHP
CMD ["php", "-S", "0.0.0.0:80"]