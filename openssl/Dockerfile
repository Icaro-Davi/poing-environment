FROM ubuntu

ARG DOMAIN

RUN apt-get update
RUN apt-get install -y openssl

WORKDIR /certbot/${DOMAIN}/

RUN openssl req -x509 -days 10 -nodes -newkey rsa:2048 \
    -keyout ./privkey.pem \
    -out ./fullchain.pem \
    -subj "/C=BR/ST=ceara/L=crato/O=poing-bot/OU=none/CN=poing.tk/emailAddress=poing.bot@gmail.com" && \
    openssl dhparam -out ./dhparam.pem 2048
