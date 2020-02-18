FROM swaggerapi/swagger-ui

ARG JWT_TOKEN
ENV JWT_TOKEN ${JWT_TOKEN}

VOLUME /usr/share/nginx/html/docs

RUN apk update && apk add gettext
COPY ./nginx.conf.tmpl /tmp/

CMD cat /tmp/nginx.conf.tmpl | envsubst \$JWT_TOKEN > /etc/nginx/nginx.conf && sh /usr/share/nginx/run.sh
