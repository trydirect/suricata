FROM ubuntu:18.04


# install requirements
RUN \
apt-get update && \
  apt-get -y upgrade && \
  apt-get install -y build-essential && \
  apt-get install -y software-properties-common && \
  apt-get install -y curl git python-pip unzip vim wget libpcre3 libpcre3-dev build-essential autoconf automake libtool libpcap-dev libnet1-dev libyaml-0-2 libyaml-dev zlib1g zlib1g-dev libmagic-dev libcap-ng-dev libjansson-dev pkg-config libnetfilter-queue-dev geoip-bin geoip-database geoipupdate apt-transport-https && \
  rm -rf /var/lib/apt/lists/*

# install suricata repo + pkg
RUN add-apt-repository -y ppa:oisf/suricata-stable \
    && apt-get update \
    && apt-get install -y suricata \
    && rm -rf /var/lib/apt/lists/*


# Install suricata dependencies
RUN pip install pyyaml \
    && pip install https://github.com/OISF/suricata-update/archive/master.zip \
    && pip install --pre --upgrade suricata-update

COPY entrypoint.sh /etc/entrypoint.sh
RUN chmod +x /etc/entrypoint.sh
COPY suricata.yaml /etc/suricata/suricata.yaml


