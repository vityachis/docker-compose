FROM nginx:1.21-alpine

MAINTAINER Viktor Chistyakov <vityachis@gmail.com>

COPY ssl_certificate.crt /etc/ssl/ssl_certificate.crt
COPY ssl_certificate.key /etc/ssl/ssl_certificate.key

COPY server.conf /etc/nginx/conf.d/default.conf

ARG ROOT_PATH
RUN sed -i 's/root _/root '$(echo $ROOT_PATH | sed 's/\//\\\//g')'/' /etc/nginx/conf.d/default.conf

# Running nginx in debug mode
CMD ["nginx", "-g", "daemon off;"]
