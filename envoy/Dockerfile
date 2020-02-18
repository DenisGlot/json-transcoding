FROM envoyproxy/envoy:v1.12.2

ARG SERVICES
ARG DESCRIPTOR_PATH
ARG APP_PORT
ENV SERVICES=${SERVICES} DESCRIPTOR_PATH=${DESCRIPTOR_PATH} APP_PORT=${APP_PORT}

VOLUME /data

RUN apt update && apt install -y gettext-base
COPY ./envoy/envoy.yaml.tmpl /tmp/

ENTRYPOINT cat /tmp/envoy.yaml.tmpl | envsubst \$APP_PORT,\$DESCRIPTOR_PATH,\$SERVICES > /etc/envoy/envoy.yaml && envoy -c /etc/envoy/envoy.yaml
