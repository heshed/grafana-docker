FROM debian:wheezy

RUN apt-get -y update
RUN apt-get -y install python wget

RUN wget http://grafanarel.s3.amazonaws.com/grafana-1.9.1.tar.gz
RUN tar xzvf grafana-1.9.1.tar.gz && rm grafana-1.9.1.tar.gz
RUN mv grafana-1.9.1 /opt/grafana

ADD config.js /opt/grafana/config.js
ADD default.json /opt/grafana/app/dashboards/default.json

ONBUILD COPY default.json /opt/grafana/app/dashboards/default.json

WORKDIR /opt/grafana

EXPOSE 8080

CMD ["python", "-m", "SimpleHTTPServer", "8081"]
