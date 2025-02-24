FROM openresty/openresty:1.25.3.1-2-alpine-fat

RUN mkdir /var/log/nginx

RUN apk add --no-cache openssl-dev
RUN apk add --no-cache git
RUN apk add --no-cache gcc

RUN luarocks install lua-resty-openidc

RUN mkdir -p /etc/nginx/include

COPY ./nginx.conf /etc/nginx/nginx.conf
COPY ./authenticate.include /etc/nginx/include/

ENTRYPOINT ["/usr/local/openresty/nginx/sbin/nginx", "-c", "/etc/nginx/nginx.conf", "-g", "daemon off;"]
