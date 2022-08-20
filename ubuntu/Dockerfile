FROM ubuntu:base

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y openjdk-11-jre-headless
RUN apt-get install -y openssh-server
RUN apt-get install -y git

RUN useradd --home '/home/jenkins' --create-home --password 'jenkins' --shell '/bin/bash' jenkins
RUN echo "jenkins:jenkins" | chpasswd

USER jenkins

RUN ssh-keygen -t rsa -N "" -f /home/jenkins/.ssh/id_rsa

USER root

RUN \
    mkdir -p /home/jenkins/.ssh \
    chmod 700 /home/jenkins/.ssh

ADD authorized_keys /home/jenkins/.ssh/
ADD ssh_config /etc/ssh/

RUN echo "PubkeyAuthentication yes" >> /etc/ssh/sshd_config
RUN echo "AuthorizedKeysFile .ssh/authorized_keys" >> /etc/ssh/sshd_config
RUN echo "PermitRootLogin no" >> /etc/ssh/sshd_config

RUN chmod 644 /etc/ssh/ssh_config
RUN chown -R jenkins:jenkins /home/jenkins/.ssh

RUN mkdir /var/run/sshd

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]