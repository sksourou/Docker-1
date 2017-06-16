# Base system is Ubuntu 16.04
FROM   debian

# Set the Teamspeak version to download
ENV TSV=3.0.13.6

# Download and install everything from the repos.
RUN    DEBIAN_FRONTEND=noninteractive \
        apt-get -y update && \
        apt-get -y install bzip2 && \
        rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
        apt-get autoremove -y && \
        apt-get clean

# Download and install TeamSpeak 3
# Add secondary/backup server as well -- allow users to choose in case of blacklisting.
ADD    http://dl.4players.de/ts/releases/${TSV}/teamspeak3-server_linux_amd64-${TSV}.tar.bz2 ./

RUN    tar jxf teamspeak3-server_linux_amd64-$TSV.tar.bz2 && \
       mv teamspeak3-server_linux_amd64 /opt/teamspeak && \
       rm teamspeak3-server_linux_amd64-$TSV.tar.bz2

ADD    ./start /start

# /start runs it.
EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 10011

RUN    useradd teamspeak && mkdir /data && chown teamspeak:teamspeak /data
USER   teamspeak
ENV LD_LIBRARY_PATH=/opt/teamspeak
CMD    ["/start"]
