FROM ubuntu:base

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y openjdk-11-jre-headless
RUN apt-get install -y openssh-server

RUN useradd --home /home/jenkins --create-home --password jenkins --shell /bin/bash jenkins

RUN \
    mkdir -p /home/jenkins/.ssh \
    chmod 700 /home/jenkins/.ssh

ADD id_rsa /home/jenkins/.ssh/
ADD id_rsa.pub /home/jenkins/.ssh/
ADD authorized_keys /home/jenkins/.ssh/
ADD ssh_config /etc/ssh/

RUN chmod 644 /etc/ssh/ssh_config
RUN chown -R jenkins:jenkins /home/jenkins/.ssh

RUN mkdir /var/run/sshd

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]