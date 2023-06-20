# Indexer Services

## Changing Passwords

There are several passwords you need to update in `docker-compose.yml`:

- Your `POSTGRES_PASSWORD` under your postgres container, as well as `--postgres-password` under coordinator container.

- Your `--secret-key` under both coordinator and proxy containers.

- Your `--jwt-secret` and `--metrics-token` under proxy container.

## Things to update when using Grafana Dashboard

- The `GF_SECURITY_ADMIN_PASSWORD` password in the Grafana container, which is in the `docker-compose-metrics.yml` file. 
This is for logging in to the Grafana dashboard.

- Update the Authorization token inside `./metrics/datasources/datasource.yml` which needs to be the same as your `--metrics-token` specified inside `docker-compose.yml` under your proxy container.

- Update the `bearer_token` inside `./metrics/prometheus.yml`. It should also be the same as `--metrics-token`.

- If you are running on linux `host.docker.internal` isn't supported so you need to specify the exact <ip>:<port> of the container in `metrics/prometheus.yml`

You can get the ip which you can get with the following command:

docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' <container_name>

## Viewing the Grafana Dashboard

After update both `docker-compose.yml` and `docker-compose-metrics.yml`, you can proceed to starting up your Grafana dashboard. 

```bash
docker-compose -f docker-compose-metrics.yml up -d
