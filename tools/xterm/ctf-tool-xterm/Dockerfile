FROM tool-xterm:latest
USER root

RUN echo 'deb http://archive.debian.org/debian/ stretch main' > /etc/apt/sources.list \
    && echo 'deb-src http://archive.debian.org/debian/ stretch main' >> /etc/apt/sources.list \
    && echo 'Acquire::Check-Valid-Until "false";' > /etc/apt/apt.conf


RUN apt-get update && apt-get install -y net-tools netcat john nmap vim hydra zip telnet ftp steghide
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y tshark

COPY sqlmap.zip /tmp
RUN unzip /tmp/sqlmap.zip -d /opt
RUN echo 'export SQLMAP_HOME=/opt/sqlmap'>> /home/yolo/.bashrc
RUN echo 'export PATH=$PATH:$SQLMAP_HOME'>> /home/yolo/.bashrc
RUN echo 'unset $(env |grep  npm_ | cut -d"=" -f1)' >> /home/yolo/.bashrc
RUN echo 'alias sqlmap=sqlmap.py'>> /home/yolo/.bashrc
USER yolo
COPY --chown=yolo:yolo challenges /home/yolo/challenges
