FROM ubuntu

ARG NGINX_VERSION

RUN apt-get update --fix-missing
RUN apt-get install -y \
    wget \
    gcc \
    g++ \
    libpcre3 libpcre3-dev \
    zlib1g zlib1g-dev \
    libssl-dev \
    make
RUN rm -rf /var/cache/apt

WORKDIR /nginx
RUN wget https://nginx.org/download/nginx-${NGINX_VERSION}.tar.gz
RUN wget \
    https://raw.githubusercontent.com/certbot/certbot/master/certbot-nginx/certbot_nginx/_internal/tls_configs/options-ssl-nginx.conf
RUN tar -xzvf ./nginx-${NGINX_VERSION}.tar.gz

COPY ./configs/nginx.conf /etc/nginx/nginx.conf

WORKDIR /nginx/nginx-${NGINX_VERSION}
RUN ./configure \
    --sbin-path=/usr/bin/nginx  \
    --conf-path=/etc/nginx/nginx.conf \
    --with-http_v2_module \
    --with-pcre \
    --with-http_ssl_module \
    --without-http_autoindex_module && \
    make && make install

CMD [ "nginx", "-g", "daemon off;" ]