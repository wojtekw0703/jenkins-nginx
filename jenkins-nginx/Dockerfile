FROM  nginx:latest
LABEL maintainer="Adam Wieczorek"

# Install NGINX
RUN apt -y update
RUN apt -y install nginx

# Add default configuration
COPY conf/jenkins.conf /etc/nginx/conf.d/jenkins.conf
COPY conf/nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

CMD ["nginx"]