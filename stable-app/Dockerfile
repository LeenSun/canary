FROM nginx:1.17.2-alpine

COPY ./dist /etc/nginx/html
COPY ./stable.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
