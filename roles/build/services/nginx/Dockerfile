FROM gcc:latest AS build
WORKDIR /build
RUN apt-get update && \
        apt-get install -y \
        libpcre3 libpcre3-dev libssl-dev
ADD ./src /app/src
WORKDIR /app/src/nginx
RUN ./auto/configure \
        --conf-path=/usr/local/nginx/nginx.conf \
        --with-http_addition_module \
        --with-http_auth_request_module \
        --with-http_dav_module \
        --with-http_flv_module \
        --with-http_gunzip_module \
        --with-http_gzip_static_module \
        --with-http_mp4_module \
        --with-http_random_index_module \
        --with-http_realip_module \
        --with-http_secure_link_module \
        --with-http_slice_module \
        --with-http_ssl_module \
        --with-http_stub_status_module \
        --with-http_sub_module \
        --with-http_v2_module \
        --with-http_v3_module \
        --with-mail_ssl_module \
        --with-stream_realip_module \
        --with-stream_ssl_module \
        --with-stream_ssl_preread_module \
        --with-stream \
        --add-module=/app/src/nginx-module-sts \
        --add-module=/app/src/nginx-module-stream-sts && make

FROM ubuntu:latest
RUN mkdir -p /usr/local/nginx && mkdir -p /usr/local/nginx/logs && mkdir -p /etc/nginx/ && mkdir /var/log/nginx/  && \
        mkdir -p /etc/nginx/conf.d && touch /usr/local/nginx/logs/error.log
WORKDIR /usr/local/nginx/
COPY --from=build /app/src/nginx/objs/nginx .
COPY ./nginx.conf /usr/local/nginx/nginx.conf
COPY ./nginx_stat.conf /etc/nginx/conf.d/nginx.conf
COPY ./src/nginx/conf/mime.types /etc/nginx/mime.types

ENTRYPOINT ["./nginx", "-g", "daemon off;"]
EXPOSE 8000 8888
