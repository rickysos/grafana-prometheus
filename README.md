## Prometheus and Grafana docker-compose stack
This is a quick way to get Prometheus, Grafana, Node-exporter and cAdvisor running. You need docker and docker-compose installed to deploy the stack

## Running the stack
```
docker-compose up -d
```

## Stopping the stack
```
docker-compose down
```

## Grafana Datasources and Dashboards
Grafana default username and password admin/admin

If you would like to automate the installation of additional dashboards just copy the Dashboard `JSON` file to `grafana/provisioning/dashboards` and it will be provisioned next time you stop and start Grafana or the docker-compose stack.

## Prometheus
If you need to make an update to Prometheus the config is located at `promethes/prometheus.ym`. The changes will be availabe the next time you stop and start Prometheus or the docker-compose stack.
You can make Prometheus data persistant by mouting a local directory to the docker container, this will allow you to compose up/down the stack without losing data. 
Add ` - /$somefolder:/prometheus` to the `docker-compose.yml` file.

Example:
```
    volumes:
      - ./prometheus:/etc/prometheus/
      - /tmp/prometheus:/prometheus
```
