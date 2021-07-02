FROM cyberduck/php-fpm-laravel:latest

RUN apt-get update && \
    apt-get install -yqq \
      libxrender1 \
      libfontconfig1 \
      libx11-dev \
      libjpeg62 \
      libxtst6 \
      fontconfig \
      libjpeg62-turbo \
      xfonts-base \
      xfonts-75dpi \
      wget \
    && wget https://github.com/wkhtmltopdf/packaging/releases/download/0.12.6-1/wkhtmltox_0.12.6-1.stretch_amd64.deb \
    && dpkg -i wkhtmltox_0.12.6-1.stretch_amd64.deb \
    && apt -f install

RUN apt-get remove libreoffice && \
    apt-get remove --purge libreoffice && \
    apt-get update && \
    apt-get install -y libreoffice --no-install-recommends && \
    apt-get install -y libreoffice-java-common

RUN apt-get install -y poppler-utils

RUN groupadd -g 1002 pdf-writers && \
    addgroup root pdf-writers && \
    newgrp pdf-writers && \
    usermod -a -G pdf-writers www-data