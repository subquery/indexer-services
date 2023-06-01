# Indexer Services

## Changing Passwords

There are several areas where you should change your password:

1. Within the containers in the `docker-compose.yaml` file. Follow the comments provided in the file for instructions on how to do this.

2. For the `GF_SECURITY_ADMIN_PASSWORD` password in the Grafana container, which is in the `docker-compose-metrics.yml` file.

## Viewing the Grafana Dashboard

After initializing the `docker-compose.yml` file, you can proceed to set up the Grafana dashboard. 

> **Important:** If your indexer proxy is running on another port, you will need to update this section in the `metrics/prometheus.yml` file.

``` yml
static_configs:
    - targets: ['host.docker.internal:80'] # this is proxy endpoint
```

After you've made the necessary adjustments, you can run the following command:

```bash
docker-compose -f docker-compose-metrics.yml up -d
