FROM postgres:12

RUN apt-get update -y\ 
    && apt-get install python3 python3-pip -y\
    && pip3 install --upgrade setuptools --break-system-packages\
    && pip3 install psycopg2-binary --break-system-packages\
    && pip3 install patroni[etcd3] --break-system-packages \ 
    && apt-get install nano
RUN mkdir /data/patroni -p \
    && chown postgres:postgres /data/patroni \
    && chmod 700 /data/patroni 

COPY patroni.yml /etc/patroni.yml
COPY patroni-entrypoint.sh ./entrypoint.sh
USER postgres

ENTRYPOINT ["bin/sh", "/entrypoint.sh"]