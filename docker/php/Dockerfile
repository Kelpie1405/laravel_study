# ベースイメージの指定
FROM php:8.4-fpm

# PHPの設定ファイルをコンテナ内にも複製
COPY ./docker/php/php.ini /usr/local/etc/php/php.ini

# composerのインストール（マルチステージビルド）
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Node.jsのインストール（マルチステージビルド）
COPY --from=node:22 /usr/local/bin /usr/local/bin
COPY --from=node:22 /usr/local/lib /usr/local/lib

# パッケージ管理ツール（apt-get）の更新＆必要パッケージのインストール
RUN apt-get update \
    # 必要なパッケージをインストール
    && apt-get -y install git zip unzip vim \
    # 以下の2つのコマンドでDockerイメージのサイズを小さくする
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    # PHPの公式Dockerイメージが提供しているコマンド(docker-php-ext-install)を利用して、PHP拡張モジュールをインストール
    && docker-php-ext-install pdo_mysql bcmath

# 作業ディレクトリの指定
WORKDIR /var/www/html