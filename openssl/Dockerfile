FROM ubuntu

ARG DOMAIN

RUN apt-get update
RUN apt-get install -y openssl

VOLUME [ "/etc/letsencrypt" ]
WORKDIR /etc/letsencrypt/${DOMAIN}/

RUN openssl req -x509 -days 10 -nodes -newkey rsa:2048 \
    -keyout /etc/letsencrypt/${DOMAIN}/privatekey.key \
    -out /etc/letsencrypt/${DOMAIN}/fullchain.crt \
    -subj "/C=BR/ST=ceara/L=crato/O=poing-bot/OU=none/CN=poing.tk/emailAddress=poing.bot@gmail.com"
