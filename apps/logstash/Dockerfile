FROM ubuntu:latest
# Create logstash image from recent ubuntu image

# Install latest patches wget
RUN apt-get update && apt-get install -y \
    && apt-get install -y wget && apt-get install -y openjdk-8-jre

# download logstash deb
RUN wget https://artifacts.elastic.co/downloads/logstash/logstash-7.6.2.deb

# Install deb
RUN dpkg -i logstash-7.6.2.deb

# place some config files in container as root
WORKDIR /etc/logstash/conf.d
RUN mkdir /var/log/logstash/ego
RUN mkdir /etc/logstash/conf.d/ego
COPY pipeline.conf .
COPY egopipe.cfg ego 
COPY egopipe ego
COPY logstash.yml /etc/logstash
RUN chmod 777 /etc/logstash/logstash.yml
WORKDIR /usr/share/logstash 
RUN bin/logstash -f /etc/logstash/conf.d --path.settings=/etc/logstash
