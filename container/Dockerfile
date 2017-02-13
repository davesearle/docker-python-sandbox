FROM ubuntu:16.04

RUN ["adduser",  "--home",  "/usr/src/app", "--system", "sandboxuser"]
RUN ["chown", "-R", "sandboxuser", "/usr/src/app"]
RUN ["chmod", "-R", "u+rwx", "/usr/src/app"]

RUN apt-get update

RUN apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_6.x | bash -
RUN apt-get install -y nodejs

RUN apt-get install -y virtualenv

RUN virtualenv -p $(which python3) /opt/sandbox

RUN apt-get install -y apparmor

COPY ./shared /usr/src/app
RUN cd /usr/src/app && npm install

COPY start.sh /
RUN chmod 755 /start.sh


CMD ["/start.sh"]
