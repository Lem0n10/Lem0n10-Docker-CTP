# User TP_Docker/HttpServer/Dockerfile
FROM httpd:2.4-alpine

# Copy custom index.html
COPY index.html /usr/local/apache2/htdocs/

# Enable proxy and proxy_http modules
RUN sed -i '/LoadModule proxy_module/s/^#//g' /usr/local/apache2/conf/httpd.conf && \
    sed -i '/LoadModule proxy_http_module/s/^#//g' /usr/local/apache2/conf/httpd.conf

# Copy custom httpd.conf
COPY httpd.conf /usr/local/apache2/conf/httpd.conf
