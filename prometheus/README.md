# Indexer metrics service

We use prometheus, grafana as the metrics service.

Uncomment the prometheus, pushgateway and grafana from `docker-compose.yml`,
```
  prometheus:
    image: prom/prometheus:latest
    ...

  pushgateway:
    image: prom/pushgateway:latest
    ...

  grafana:
    image: grafana/grafana:latest
    ...

  proxy:
    ...
    command:
      ...
      - --pushgateway-endpoint=http://indexer_pushgateway:9091 # the indexer-pushgateway endpoint, if need, uncomment it
```

## Configure grafana
1. visit grafana at `http://localhost:3000`
2. Login and setup the password
3. `Dashboards` -> `New dashboard` -> `Add a new panel`
4. Select `query_count` in `Metric`, and select `exported_instance` in `Label filters`, and then select value your project ID
5. Click query and Refresh it
6. Save this panel

