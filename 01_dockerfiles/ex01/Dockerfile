FROM debian

RUN apt-get update && apt-get install wget bzip2 -y
RUN wget https://files.teamspeak-services.com/releases/server/3.9.1/teamspeak3-server_linux_amd64-3.9.1.tar.bz2
RUN tar xvjf teamspeak3-server_linux_amd64-3.9.1.tar.bz2
RUN cd teamspeak3-server_linux_amd64 && touch .ts3server_license_accepted
WORKDIR teamspeak3-server_linux_amd64
CMD sh ts3server_minimal_runscript.sh
#docker run -p 10.11.2.15:9987:9987/udp -p 10.11.2.15:10011:10011 -p 10.11.2.15:30033:30033 <image name>
