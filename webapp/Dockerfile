FROM centos:centos7
MAINTAINER Gennadii Altukhov <galt@redhat.com>

# defaults; will be overwritten by docker-compose.env
ENV POSTGRESQL_HOST=database
ENV POSTGRESQL_PORT=5432
ENV POSTGRESQL_USER=vmaas_user
ENV POSTGRESQL_PASSWORD=vmaas_passwd
ENV POSTGRESQL_DATABASE=vmaas

RUN yum -y update && yum -y install python-tornado python-psycopg2 postgresql && rm -rf /var/cache/yum/*

ADD ./wait-for-postgres.sh /app/wait-for-postgres.sh
ADD ./entrypoint.sh /app/
ADD ./*.py /app/
ADD ./vmaas /app/

EXPOSE 8079 8080

CMD ["/app/entrypoint.sh"]
