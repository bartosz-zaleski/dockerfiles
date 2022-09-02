FROM jenkins/ubuntu:latest

RUN apt-get install -y python3-pip
RUN pip3 install flask

ENTRYPOINT [ "flask --app " ]