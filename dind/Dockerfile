FROM docker:latest

RUN apk update
RUN apk add openjdk17-jre-headless
RUN apk add openssh-server
RUN apk add git

RUN adduser --gecos "" --disabled-password --home /home/jenkins --shell /bin/sh jenkins
RUN chpasswd jenkins:jenkins

RUN \
    mkdir -p /home/jenkins/.ssh \
    chmod 700 /home/jenkins/.ssh

ADD authorized_keys /home/jenkins/.ssh/
ADD ssh_config /etc/ssh/
ADD sshd_config /etc/ssh/

RUN chmod 644 /etc/ssh/ssh_config
RUN chown -R jenkins:jenkins /home/jenkins/.ssh

RUN mkdir /var/run/sshd
RUN cd /etc/ssh ; ssh-keygen -A

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]