# Description: MariaDB Dockerfile

# pull base image
FROM debian:bullseye

# run command in container for update /upgrade system package
RUN apt-get update && apt-get upgrade -y

# install the required packages, netcat pings mariaDB makes sure it is running before Wordpress
RUN apt-get install -y mariadb-server netcat

# copy file from host to container
COPY ./conf/mdb-conf.sh /mdb-conf.sh

# set permissions to read and write
RUN chmod +x /mdb-conf.sh

# define entrypoint command to run when the container starts
ENTRYPOINT ["./mdb-conf.sh"]