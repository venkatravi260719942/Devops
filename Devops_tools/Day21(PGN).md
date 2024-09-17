# Day 21: Prometheus, Grafana, and Node Exporter

## 1. Introduction to Prometheus

### What is Prometheus?
**Prometheus** is an open-source monitoring and alerting toolkit designed for reliability and scalability. It is used to monitor systems, collect metrics, and trigger alerts based on defined conditions.

### Key Features:
- **Time-Series Database**: Stores metrics data with timestamps.
- **Pull Model**: Prometheus scrapes targets to collect metrics, as opposed to receiving pushed data.
- **PromQL**: Query language used to retrieve and manipulate time-series data.
- **Alerting**: Integrated alert manager for sending notifications when certain conditions are met.
  
---

## 2. Introduction to Grafana

### What is Grafana?
**Grafana** is an open-source platform for monitoring and observability. It provides powerful dashboards and visualization tools for understanding and analyzing metrics.

### Key Features:
- **Visualization**: Create interactive and flexible dashboards with a wide range of charts and graphs.
- **Integration with Prometheus**: Seamlessly integrates with Prometheus to visualize collected metrics.
- **Alerting**: Set up alerts based on visualized data.

---

## 3. Introduction to Node Exporter

### What is Node Exporter?
**Node Exporter** is a Prometheus exporter that exposes hardware and operating system-level metrics (like CPU, memory, and disk usage) from a machine for Prometheus to scrape.

### Key Features:
- **System Metrics**: Provides detailed information about the machine’s performance and status.
- **Metrics Format**: Exposes metrics in a format that Prometheus can easily scrape and process.

---

## 4. Setting Up Prometheus

### A. Install Prometheus
1. **Download Prometheus**:
   - Visit the [Prometheus downloads page](https://prometheus.io/download/) and get the latest version:
     ```bash
     wget https://github.com/prometheus/prometheus/releases/download/v<version>/prometheus-<version>.linux-amd64.tar.gz
     ```
   - Extract the tarball:
     ```bash
     tar -xvf prometheus-<version>.linux-amd64.tar.gz
     cd prometheus-<version>.linux-amd64
     ```

2. **Run Prometheus**:
   - Start Prometheus using the following command:
     ```bash
     ./prometheus --config.file=prometheus.yml
     ```

3. **Access Prometheus UI**:
   - Prometheus runs on `http://localhost:9090`. Access it via your browser to check the status.

### B. Configuring Prometheus to Scrape Node Exporter
- Add the Node Exporter to the `prometheus.yml` configuration file:
  ```yaml
  scrape_configs:
    - job_name: 'node_exporter'
      static_configs:
        - targets: ['localhost:9100']

---
## 5. Setting Up Node Exporter
### A. Install Node Exporter

 **1.Download Node Exporter:**
Download the latest version from the Prometheus Node Exporter page:

```bash
wget https://github.com/prometheus/node_exporter/releases/download/v<version>/node_exporter-<version>.linux-amd64.tar.gz
```
- **Extract the tarball:**

```bash
tar -xvf node_exporter-<version>.linux-amd64.tar.gz
cd node_exporter-<version>.linux-amd64
```

 **2.Run Node Exporter:**

- Start Node Exporter:

```bash
./node_exporter
```
 **3.Access Node Exporter Metrics:**

- Node Exporter runs on http://localhost:9100/metrics. Visit the URL to view the exposed metrics.

## 6. Setting Up Grafana
### A. Install Grafana
- **1. Add the Grafana APT repository (on Debian/Ubuntu):**
```bash
sudo apt update
sudo apt install -y software-properties-common
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
```
- **2. Install Grafana:**

- Install Grafana using the package manager:
```bash
sudo apt update
sudo apt install grafana
```
- **3. Start Grafana:**

- Start the Grafana service
```bash
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
```
- **4. Access Grafana UI:**

- Open Grafana at http://localhost:3000. The default username and password are both admin.
---
## 7. Integrating Prometheus with Grafana

### A. Add Prometheus as a Data Source
- **1. Log into Grafana and go to Configuration -> Data Sources.**
- **2. Add Prometheus by selecting it from the list of data sources and setting the URL to http://localhost:9090.**

### B. Creating Dashboards
#### 1. Create a New Dashboard:**

- Go to Create -> Dashboard, then Add New Panel.
PromQL Queries:

#### 2. PromQL Queries:

- Write a query to visualize data. For example, to monitor CPU usage from Node Exporter:
```promql
node_cpu_seconds_total{mode="idle"}
```

#### 3. Save and Explore:
- Customize your panel to create graphs, gauges, or tables, and save the dashboard for continuous monitoring.

## 8. Setting Up Alerts in Grafana
### A. Define an Alert Rule
**1. Create an Alert:**

- Go to your dashboard panel, click on the alerting tab, and define a rule. For example, set an alert when CPU usage exceeds a threshold.

**2. Configure Notification Channels:**

- Set up channels for receiving alerts via email, Slack, or other tools.

### B. Testing Alerts
**1. Test Alert Conditions:**
- Trigger alerts based on the metrics you are monitoring, and ensure that you receive notifications as expected.

## 9. Best Practices
### A. Monitoring with Prometheus and Grafana
- Use Prometheus to scrape system metrics with Node Exporter, and visualize them in Grafana for better understanding and tracking.
### B. Define Clear Alerts
- Set up alerts for key metrics like CPU usage, memory consumption, and disk space to get early notifications before issues impact the system.

---
# Summary
Today, we explored Prometheus, Grafana, and Node Exporter, which are essential tools for monitoring system performance and health. We covered the installation and configuration of each tool, how to collect and visualize system metrics, and how to set up alerts for proactive monitoring.

## Key Takeaways:

Prometheus is used to scrape and store time-series metrics.
Grafana provides powerful visualization of metrics.
Node Exporter exposes system-level metrics for Prometheus to scrape.

### Next Session
In the next session, we will dive into Backup and Snapshot to understand data backup strategies in AWS.

---
#### Thank you!