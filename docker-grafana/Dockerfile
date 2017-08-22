FROM ubuntu:14.04

RUN apt-get update && apt-get -y install libfontconfig wget adduser openssl ca-certificates
RUN wget https://s3-us-west-2.amazonaws.com/grafana-releases/release/grafana_4.4.3_amd64.deb
RUN dpkg -i grafana_4.4.3_amd64.deb

ADD grafana.ini /usr/share/grafana/conf/defaults.ini
ADD start /start

RUN chmod 755 /start

VOLUME ["/var/lib/grafana"]
VOLUME ["/var/log/grafana"]

WORKDIR /usr/share/grafana

EXPOSE 3000

CMD ["/start"]
