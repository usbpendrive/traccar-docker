FROM openjdk:8-jre-alpine

ENV TRACCAR_VERSION 3.17

WORKDIR /opt/traccar

RUN set -ex && \
    apk add --no-cache wget && \
    \
    wget -qO /tmp/traccar.zip https://github.com/usbpendrive/traccar-release/archive/traccar-3.17.zip && \
    unzip -qo /tmp/traccar.zip -d /opt/traccar && \
    rm /tmp/traccar.zip && \
    \
    apk del wget

RUN chgrp -R 0 /opt/traccar/logs && chmod -R g=u /opt/traccar/logs
RUN chgrp -R 0 /opt/traccar/data && chmod -R g=u /opt/traccar/data

EXPOSE 8082

ENTRYPOINT ["java"]

CMD ["-Djava.net.preferIPv4Stack=true", "-Xms512m", "-Xmx512m", "-jar", "tracker-server.jar", "conf/traccar.xml"]
