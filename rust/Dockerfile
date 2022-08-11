FROM jenkins/ubuntu:latest

USER jenkins

ADD rustup.sh /home/jenkins

RUN /home/jenkins/rustup.sh -y
RUN rm -f /home/jenkins/rustup.sh

USER root
RUN echo "export PATH=/home/jenkins/.cargo/bin:${PATH}" >> /etc/environment

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]