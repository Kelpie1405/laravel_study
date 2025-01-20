# ベースイメージの指定
FROM nginx:1.18-alpine

# タイムゾーンの指定
ENV TZ='Asia/Tokyo'

# nginxの設定ファイルをコンテナ内にも複製
COPY ./docker/nginx/*.conf /etc/nginx/conf.d/

# 作業ディレクトリの指定
WORKDIR /var/www/html