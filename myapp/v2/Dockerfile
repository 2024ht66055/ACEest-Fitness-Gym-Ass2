FROM nginx:alpine
RUN echo "Hello from Version 2" > /usr/share/nginx/html/index.html
RUN sed -i 's/access_log off;/access_log \/var\/log\/nginx\/access.log;/' /etc/nginx/nginx.conf