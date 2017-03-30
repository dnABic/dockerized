FROM alpine:3.4

ENV NEXUS_VERSION="3.2.1-01" \
  NEXUS_DATA="/nexus-data" \
  JKS_PASSWORD="Kr4st4v-4c"

RUN set -x \
  && apk --no-cache add \
    openjdk8-jre-base \
    openssl \
    su-exec \
  && mkdir "/opt" \
  && wget -qO - "https://download.sonatype.com/nexus/3/nexus-${NEXUS_VERSION}-unix.tar.gz" \
  | tar -zxC "/opt" \
  && adduser -S -h ${NEXUS_DATA} nexus \
  && mkdir -p "${NEXUS_DATA}" \
  && chown -R nexus "${NEXUS_DATA}"

RUN mv /opt/nexus-${NEXUS_VERSION}/bin/nexus.vmoptions /opt/nexus-${NEXUS_VERSION}/bin/nexus.vmoptions-orig
RUN ln -s /nexus.vmoptions /opt/nexus-${NEXUS_VERSION}/bin/nexus.vmoptions

EXPOSE 8081 5000

WORKDIR "/opt/nexus-${NEXUS_VERSION}"

VOLUME ${NEXUS_DATA}

CMD ["su-exec", "nexus", "bin/nexus", "run"]
