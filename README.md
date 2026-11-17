## Monitoring Metrics, Logs, Traces, Profiles with Prometheus and Grafana stack


Below is the complete setup for using the Prometheus and Grafana stack to monitor metrics, logs, traces, and profiles. All relevant Docker images are used to demonstrate this setup.  


**Setup**  
Run the below commands to download the demo repository and run Prometheus and Grafana stack.  
```bash
#Downloading the repository
git clone git@github.com:hiepdng/monitoring_metric_logs_traces_profiles_with_prometheus_grafana_stack.git

#Creating volumes
cd monitoring_metric_logs_traces_profiles_with_prometheus_grafana_stack
mkdir prometheus_data
sudo chown -R nobody:nogroup prometheus_data
mkdir grafana_data
sudo chown -R 472:472 grafana_data
mkdir loki_data
sudo chown -R 10001:10001 loki_data
mkdir alloy_data
sudo chown -R 473:473 alloy_data
mkdir tempo_data
sudo chown -R 10001:10001 tempo_data
mkdir pyroscope_data
sudo chown -R 10001:10001 pyroscope_data

#Running containers
docker compose up -d
```
**Access Grafana web:**  
Go to http://localhost:3000/ to access your local Grafana webpage and monitor Drilldown Metrics, Logs, Traces and Profiles.  

To view specific container webpages:  
- Prometheus: http://localhost:9090/
- Node-exporter: http://localhost:9100/ or http://localhost:9100/metrics
- Alloy: http://localhost:12345/ or http://localhost:12345/graph or http://localhost:12345/metrics
- Loki: http://localhost:3100/ready or http://localhost:3100/metrics
- Tempo: http://localhost:3200/ready or http://localhost:3200/metrics
- Pyroscope: http://localhost:4040/
- Alertmanager: http://localhost:9093/

**View Grafana Drilldown Metrics, Logs, Traces and Profiles:**  
To view a corresponding page:  
- Go to http://localhost:3000/  
- Click on **Drilldown** ➔ **Metrics**, **Logs**, **Traces** or **Profiles**  
- Note:
  - **Metrics** requires **Prometheus** data source.  
  - **Logs** requires **Loki** data source.  
  - **Traces** requires **Tempo** data source.  
  - **Profiles** required **Pyroscope** data source.
  All of the required data sources are included in the grafana-datasources.yaml file.  If a data source is missing or if you want to modify data source options,  click on **Connections**➔**Data sources**➔**Add new data source** and enter properly options.  



