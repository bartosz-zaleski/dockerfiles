FROM jenkins/ubuntu:latest


RUN apt-get install -y python3-pip
RUN apt-get install -y  libglib2.0-dev
RUN pip3 install lywsd03mmc

ENTRYPOINT ["lywsd03mmc"]