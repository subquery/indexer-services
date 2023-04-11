# indexer-services

Maintain the docker compose file for starting indexer services

## Step
0. Preinstall `docker`, `docker-compose` and `git`
1. Download the repository `git clone https://github.com/subquery/indexer-services.git`
2. Run `docker-compose up`, Run as a daemon, use `docker-compose up -d`
3. Open `http://localhost:8000` to configure the services

If you want to use metrics (prometheus & grafana), follow [this tutorial](./prometheus)
