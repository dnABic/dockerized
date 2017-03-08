FROM rabbitmq:3.6-management

COPY rabbitmq-cluster /usr/local/bin/
COPY exporter/prometheus-3.1.0.ez /plugins/
COPY exporter/prometheus_process_collector-1.0.2.ez /plugins/
COPY exporter/prometheus_rabbitmq_exporter-v3.6.5.9.ez /plugins/

EXPOSE 5672 15672 25672 4369 9100 9101 9102 9103 9104 9105
CMD ["rabbitmq-cluster"]
