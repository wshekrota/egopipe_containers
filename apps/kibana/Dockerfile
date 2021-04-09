FROM ubuntu:latest
# Create Kibana container

# Install latest patches wget
RUN apt-get update && apt-get install -y \
    && apt-get install -y wget && apt-get install -y openjdk-8-jre

# download kibana deb
RUN wget https://artifacts.elastic.co/downloads/kibana/kibana-7.7.0-amd64.deb

# Install deb
RUN dpkg -i kibana*.deb

# place some config files in container as root
WORKDIR /etc/kibana
COPY kibana.yml .
WORKDIR /usr/share/kibana
RUN bin/kibana -c /etc/kibana/kibana.yml --allow-root

