# pull the base image
FROM debian:bullseye

# update and upgrade the system
RUN apt-get update && apt-get upgrade -y

# install the required packages
RUN apt-get install -y nginx openssl

#create the ssl directory
RUN mkdir -p /etc/nginx/ssl

# generate ssl certificate, x509 self sign certificate
RUN openssl req -x509 -nodes -out /etc/nginx/ssl/inception.crt -keyout \
    /etc/nginx/ssl/inception.key -subj "/C=MY/ST=KL/L=KL/O=42kl/OU=42kl/CN=sulim.42.kl/UID=sulim"
	
#copy the nginx configuration file
COPY ./conf/nginx.conf /etc/nginx/nginx.conf

#create the wordpress directory
RUN mkdir -p /var/www/wordpress

# change ownership recursively (apply to all files / subdirectories) of the wordpress directory to www-data
RUN chown -R www-data:www-data /var/www/wordpress

#define the command to run when the container starts. Nginx runs in the foreground - allowing docker container to stay alive
CMD ["nginx", "-g", "daemon off;"]