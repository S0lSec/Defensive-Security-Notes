# SIEM
## What is a SIEM?
- **Security Information and Event Management** merges the management of security data and supervision of security events.
- Has core functionalities such as:
	- Collection and administration of log events
	- Examine log events
	- Supplementary data from various sources
## How does a SIEM work?
A SIEM functions by gathering data from variety of sources, such as PCs, network devices, server, etc. This data is then standardized and consolidated to facilitate ease of analysis.

If a possible security incident or event occurs the SIEM alerts notify security operators/monitoring personnel.
## Business Requirements & Use Cases
- Log aggregation & Normalization
- Threat Alerting
- Contextualization & Response
- Compliance
## Data Flows Within a SIEM
1. SIEM solution ingest logs from various data sources. (This is known as data ingestion or data collection)
2. The gathered data is processes and normalized to be understood by the SIEM correlation engine.
3. SOC teams utilize the normalized data collected by the SIEM to create various detection rules, dashboards, visualizations, alerts and incidents.
# Elastic Stack
An open-source collection of mainly three applications (Elasticsearch, Logstash and Kibana) that work to offer users comprehensive search and visualisation capabilities for real-time analysis and exploration of log file sources.
![[Pasted image 20260625120755.png]]
Elastic stack can be enhanced in resource-intensive environments with the addition of Kafka, RabbitMQ and Redit for buffering and resiliency. Nginx can also be included for security.
![[Pasted image 20260625120909.png]]
## Elastic Stack Components
**Elasticsearch**:
- Distributed and JSON-based search engine, designed with RESTful APIs.
- Handles indexing, storing and querying
- Empowers users to conduct sophisticated queries and perform analytics operations on the log file records processed by Logstash
**Logstash**:
- Responsible for collecting, transforming and transporting log file records
- Has the ability to consolidate data from various sources and normalize them
- Operates in three main areas:
	- **Process input**
	- **Transform and enrich log records**
	- **Send log records to Elasticsearch**
**Kibana**:
- Visualization tool for Elasticsearch documents
- Simplifies the comprehension of query results using tables, charts and custom dashboards
**Beats**:
- Lightweight, single-purpose, data shippers
- Designed to be installed on remote machines to forward logs and metrics to either Logstash or Elasticsearch directly

`Beats` -> `Logstash` -> `Elasticsearch` -> `Kibana`
![[Pasted image 20260627214318.png]]
`Beats` -> `Elasticsearch` -> `Kibana`
![[Pasted image 20260627214325.png]]
# KQL
(Kibana Query Language)
- Queries are composed of `field:value` pairs with the field representing the data attribute and the value representing the data your searching for. (Example: `event.code:4625`)
- You can search free text, allowing you to search a specific term
- Logical operators are supported (AND, OR, NOT)
- Comparison operators are supported
- Wildcards and regular expressions are supported (Example `event.code:4625 AND user.name: admin*`)
# Elastic Common Schema (ECS)
A Shared and extensible vocabulary for events and logs across the Elastic Stack, which ensures consistent field formats across different data sources.
When it comes to KQL searches within the Elastic Stack using ECS fields presents several key advantages:
- **Unified Data View**: ECS enforces a structured and consistent approach to data, allowing for unified views across multiple data sources.
- **Improved Search Efficiency**: By standardizing the field names across different data types, ECS simplifies the process of writing queries in KQL.
- **Enhanced Correlation**: ECS allows for easier correlation of events across different sources, which is pivotal in cyber security investigations.
- **Better Visualizations**: Consistent field naming conventions improve the efficacy of visualizations in Kibana.
- **Interoperability with Elastic Solutions**: Using ECS fields ensures full compatibility with advanced Elastic Stack features and solutions, such as Elastic Security, Elastic Observability and Elastic Machine Learning.
- **Futer-proofing**: As ECS is the foundational schema across the Elastic Stack, adopting ECS ensures future compatibility with enhancements and new features that are introduced into the Elastic ecosystem.
# SOC Definition & Fundamentals
SOC or Security Operations Center is an essential facility that houses a team of information security experts responsible for continuously monitoring and evaluating an organizations security status.
