FROM ubuntu:base

ARG ssh_pub_key

RUN apt-get update
RUN apt-get upgrade
RUN apt-get install -y openjdk-11-jre-headless
RUN apt-get install -y openssh-server

#TODO use --skel --create-home 

RUN useradd --home /home/jenkins  jenkins

RUN mkdir -p /root/.ssh
RUN touch /root/.ssh/authorized_keys \
    chmod 600 /root/.ssh/authorized_keys \
    echo "${ssh_pub_key}" >> /root/.ssh/authorized_keys

CMD /bin/bash