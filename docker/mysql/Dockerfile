# ベースイメージの指定
FROM mysql:8.4

# タイムゾーンの指定
ENV TZ='Asia/Tokyo'

# mysqlの設定ファイルをコンテナ内にも複製
COPY ./docker/mysql/my.cnf /etc/my.cnf