FROM ubuntu:14.04
MAINTAINER gamzabaw@gmail.com

ENV PG_VERSION=9.6 \
    PG_USER=postgres \
    PG_HOME="/var/lib/postgresql"

ENV PG_CONFDIR="/etc/postgresql/${PG_VERSION}/main" \
    PG_BINDIR="/usr/lib/postgresql/${PG_VERSION}/bin" \
    PG_DATADIR="${PG_HOME}/${PG_VERSION}/main"

RUN apt-get update \
 && apt-key add ACCC4CF8.asc \
 && echo 'deb http://apt.postgresql.org/pub/repos/apt/ trusty-pgdg main' > /etc/apt/sources.list.d/pgdg.list \
 && apt-get install -y postgresql-${PG_VERSION} postgresql-client-${PG_VERSION} postgresql-contrib-${PG_VERSION} \
 && rm -rf ${PG_HOME} \
 && rm -rf /var/lib/apt/lists/*

COPY start /start
RUN chmod 755 /start

EXPOSE 5432/tcp
VOLUME ["${PG_HOME}", "/run/postgresql"]
CMD ["/start"]
