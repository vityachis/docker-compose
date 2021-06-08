FROM nginx:1.21-alpine

COPY server.conf /etc/nginx/conf.d/default.conf

# Running nginx in debug mode
CMD ["nginx", "-g", "daemon off;"]
