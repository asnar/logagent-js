FROM node:8.11-alpine

ENV REGION="US"

RUN \
  apk add --update bash tini && \
  rm -rf /var/cache/apk/*

RUN \
  npm install -g --unsafe-perm @sematext/logagent && \
  mkdir -p /etc/sematext && \
  mkdir -p /opt/logagent && \
  touch /opt/logagent/patterns.yml && \
  rm -rf /tmp/*

COPY patterns.yml /opt/logagent/patterns.yml
COPY run.sh /run.sh
RUN chmod +x /run.sh

ENTRYPOINT ["/sbin/tini", "--"]
CMD ["/run.sh"]
