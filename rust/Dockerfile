FROM jenkins/ubuntu:latest

USER jenkins

ADD rustup.sh /home/jenkins

RUN /home/jenkins/rustup.sh -y
RUN rm -f /home/jenkins/rustup.sh
ENV PATH="/home/jenkins/.cargo/bin:${PATH}"

USER root

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]