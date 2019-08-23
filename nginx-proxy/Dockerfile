FROM openresty/openresty:1.15.8.2-alpine
RUN set -ex && apk --no-cache add sudo && \
    echo "nobody ALL=(root) NOPASSWD:/usr/local/openresty/nginx/sbin/nginx -s reload" > /etc/sudoers.d/nobody && \
    chmod 0440 /etc/sudoers.d/nobody

EXPOSE 8088
CMD ["nginx", "-g", "daemon off;"]
