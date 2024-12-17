#pull the base image
FROM debian:bullseye

RUN apt-get update && apt-get upgrade -y

#install the required packages
RUN apt-get install -y curl php php7.4-fpm php-mysql mariadb-client wget vim zsh git netcat mycli

COPY ./conf/wp_conf.sh /

#change permission of script to be executable
RUN chmod +x wp_conf.sh

# entrypoint to run when container starts
ENTRYPOINT ["./wp_conf.sh"]