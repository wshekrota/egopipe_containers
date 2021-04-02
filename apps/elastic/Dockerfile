FROM ubuntu:latest
# Create single elastic node from recent ubuntu image

# Install latest patches wget
RUN apt-get update && apt-get install -y \
    && apt-get install -y wget 

# download elasticsearch deb
RUN wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.7.1-amd64.deb 

# Install deb
RUN dpkg -i elasticsearch*.deb

# place some config files in container as root
WORKDIR /etc/elasticsearch
COPY elasticsearch.yml . 
RUN chmod 666 /etc/elasticsearch/elasticsearch.yml
RUN chown root:elasticsearch /etc/elasticsearch/elasticsearch.yml

RUN apt-get install nano -y 
#RUN sysctl -w m.max_map_count=262144

# become non root user elastic will not run as root
USER elasticsearch 

# Start elasticsearch
WORKDIR /usr/share/elasticsearch  
RUN bin/elasticsearch
