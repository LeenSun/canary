FROM openresty/openresty:alpine

COPY ./proxy.conf /etc/nginx/conf.d/default.conf

EXPOSE 8088
CMD ["nginx", "-g", "daemon off;"]
