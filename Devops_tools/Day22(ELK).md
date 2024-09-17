# Day 22: ELK Stack (Elasticsearch, Logstash, Kibana)

## 1. Introduction to ELK Stack

### What is the ELK Stack?
The **ELK Stack** is a collection of three open-source products:
- **Elasticsearch**: A search and analytics engine.
- **Logstash**: A server-side data processing pipeline that ingests data, transforms it, and sends it to a target (e.g., Elasticsearch).
- **Kibana**: A visualization tool that works on top of Elasticsearch to help analyze and display data through charts and dashboards.

The ELK Stack is widely used for log analysis, monitoring, and searching large volumes of data.

---

## 2. Elasticsearch

### What is Elasticsearch?
**Elasticsearch** is a distributed, RESTful search and analytics engine capable of storing, searching, and analyzing large volumes of data in real-time.

### Key Features:
- **Full-Text Search**: Performs searches across multiple fields of data.
- **Distributed Architecture**: Scales horizontally with ease, distributing data across clusters.
- **Real-Time Analytics**: Analyzes logs and metrics instantly as they are ingested.

### Basic Elasticsearch Commands:
- **Search Query**:
  ```bash
  curl -X GET "localhost:9200/index_name/_search?q=field:value&pretty"

- **Insert Data:**
```bash
curl -X POST "localhost:9200/index_name/_doc/1" -H 'Content-Type: application/json' -d'
{
  "field": "value"
}'
```
- **Delete Data:**
```bash
curl -X DELETE "localhost:9200/index_name/_doc/1"
```

## 3. Logstash
### What is Logstash?

***Logstash*** is a data collection and processing pipeline that ingests data from various sources, transforms it, and sends it to a destination such as Elasticsearch.

### Key Features:
- Data Ingestion: Collects data from various sources (e.g., logs, metrics).
- Processing and Transformation: Filters and processes data using plugins.
- Output: Sends processed data to Elasticsearch or other storage systems.

### Logstash Configuration Example:
Create a configuration file (logstash.conf) with the following content:
```bash
input {
  file {
    path => "/var/log/syslog"
    start_position => "beginning"
  }
}

filter {
  grok {
    match => { "message" => "%{SYSLOGLINE}" }
  }
}

output {
  elasticsearch {
    hosts => ["localhost:9200"]
    index => "syslog-%{+YYYY.MM.dd}"
  }
}
```
- **Start Logstash:**
```bash
sudo systemctl start logstash
sudo systemctl enable logstash
```
## 4. Kibana
### What is Kibana?
Kibana is a visualization tool that works on top of Elasticsearch, allowing users to create and view charts, graphs, and dashboards for their data.

### Key Features:
- **Visualizations:** Create bar charts, line graphs, pie charts, and more.
- **Dashboards:** Combine multiple visualizations into a single, interactive dashboard.
- **Search and Filtering:** Analyze data from Elasticsearch with queries and filters.

### Creating a Dashboard in Kibana:
- **1.Access Kibana:** Open http://localhost:5601 in your browser.
- **2.Create Visualizations:**
- Go to Visualize and click Create Visualization.
- Choose a visualization type and create visualizations based on your data.
- **Build Dashboards:**
- Go to Dashboard and click Create New Dashboard.
- Add your visualizations to the dashboard and arrange them as needed.
- Save the dashboard for future use.

## 5. Setting Up the ELK Stack
### A. Installing Elasticsearch:
```bash
sudo apt update
sudo apt install elasticsearch
sudo systemctl start elasticsearch
sudo systemctl enable elasticsearch
```
### B. Installing Logstash:
```bash
sudo apt update
sudo apt install logstash
sudo systemctl start logstash
sudo systemctl enable logstash
```
### C. Installing Kibana:
```bash
sudo apt update
sudo apt install kibana
sudo systemctl start kibana
sudo systemctl enable kibana
```
## 6. Best Practices
### A. Data Retention:
- Configure data retention policies in Elasticsearch to manage disk space and keep only necessary logs.
### B. Monitoring and Alerts:
- Use Kibana and Elasticsearch to monitor system performance and set up alerts for critical events or thresholds.
### C. Security:
- Implement security best practices for Elasticsearch, including access controls, encryption, and secure communication.

## 7. Conclusion
The **ELK Stack** provides a powerful solution for log management, data analysis, and visualization. By integrating Elasticsearch, Logstash, and Kibana, you can efficiently handle and analyze large volumes of data, gaining valuable insights into system performance and operations.

---
#### Thank you!