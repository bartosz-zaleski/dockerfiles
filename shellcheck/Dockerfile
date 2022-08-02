FROM ubuntu:latest

RUN apt-get update
RUN apt-get upgrade
RUN apt-get install -y shellcheck
RUN apt-get install -y openjdk-11-jre-headless

CMD exec $*