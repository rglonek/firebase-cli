FROM ubuntu:20.04

# non-interactive package install
ENV DEBIAN_FRONTEND=noninteractive

# for all stuff
WORKDIR /firebase

# install curl, tools and nodesource
RUN apt update && apt install -y curl vim less
RUN curl -sL https://deb.nodesource.com/setup_16.x -o /tmp/nodesource_setup.sh
RUN /bin/bash /tmp/nodesource_setup.sh

# install nodejs and update npm
RUN apt install -y nodejs gcc g++ make
RUN npm install -g npm@8.8.0

# install firebase-tools
RUN npm install -g firebase-tools

# welcome message
COPY welcome.msg /etc/welcome.msg
RUN echo "cat /etc/welcome.msg" >> ~/.bashrc

# entrypoint
CMD /bin/bash
