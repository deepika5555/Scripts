# Steps

1. docker pull prom/prometheus
2. docker run -d --name prometheus -p 9090:9090 -v <PATH_TO_prometheus.yml_FILE>:/etc/prometheus/prometheus.yml prom/prometheus --config.file=/etc/prometheus/prometheus.yml
3. docker run -d --name grafana -p 3000:3000 grafana/grafana
