FROM openresty/openresty:1.15.8.1-3-bionic

COPY ./proxy.conf /etc/nginx/conf.d/default.conf

EXPOSE 8088
CMD ["nginx", "-g", "daemon off;"]
