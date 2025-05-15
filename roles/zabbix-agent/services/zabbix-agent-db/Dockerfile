FROM zabbix/zabbix-agent
USER root
COPY ./zabbix-repo/templates/db/postgresql_agent/postgresql/ /var/lib/zabbix/postgresql/
COPY ./zabbix-repo/templates/db/postgresql_agent/template_db_postgresql.conf /etc/zabbix/zabbix_agentd.d/template_db_postgresql.conf
RUN apk update && apk --update add postgresql-client