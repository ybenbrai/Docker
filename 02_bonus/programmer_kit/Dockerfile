FROM ubuntu

RUN apt-get update && apt-get upgrade -y
RUN apt-get install vim gcc git -y
RUN apt-get update
RUN apt-get install nodejs -y && apt-get update
RUN apt-get install npm -y && apt-get update
RUN apt-get install clamav -y && apt-get update
RUN apt-get install nginx -y && apt-get update && apt-get upgrade -y
CMD bash
