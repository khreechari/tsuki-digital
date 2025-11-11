FROM debian:bookworm-slim

ENV  TECHWISE_NGINX_SHA256    4f8a6d0567ad02163c792b7de1663c29f065db1ac6227e453b7ce5ecd1f9a0aa

RUN  apt update && apt -y upgrade && apt -y install wget nginx-common libpcre3 libgeoip-dev \
     && cd && wget https://github.com/khreechari/tsuki-digital/releases/download/v1.29.3/nginx-1.29.3.amd64-linux-gnu.deb \
     && echo "$TECHWISE_NGINX_SHA256 nginx-1.29.3.amd64-linux-gnu.deb" | sha256sum -c - && \
     dpkg -i nginx-1.29.3.amd64-linux-gnu.deb \
     && rm -rf nginx-1.29.3.amd64-linux-gnu.deb

RUN  mkdir /usr/local/nginx \
     && touch /usr/local/nginx/uwsgi_temp

COPY ./nginx/nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

STOPSIGNAL SIGQUIT

CMD ["nginx", "-g", "daemon off;"]
