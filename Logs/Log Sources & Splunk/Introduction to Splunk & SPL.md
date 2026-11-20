Splunk is a data analytics software solution, which multiple sources have their logs collected and ingested by splunk.
![[Pasted image 20260706204736.png]]![[Pasted image 20260706204740.png]]

**Forwarders**: Responsible for data collection
- **Universal Forwarder (UF)**: Collects data and forwards it without any preprocessing
- **Heavy Forwarder (HF)**: Collects data, parses data then forwards. Usually collects from remote sources.
- **HTTP  Event Collectors (HECs)**: Collect data from applications in a scalable manner

**Indexers**: 
- Receive data from forwarders, organize it and store in indexes.
- While indexing, generates sets of directories categorized by age.
- Each directory holds compressed data and corresponding indexes.
- **Process search queries from users and return results**

**Search Heads**
- Coordinate search jobs, dispatching them to the indexes and merging the results
- Provide an interface for users to interact with

**Deployment Server**:
- Manages the configuration for forwarders, distributing apps and updates

**Cluster Master**:
- Coordinates the activities of indexers in a clustered environment, ensuring data replication and search affinity

**License Master**:
- Manages the licensing details of the Splunk platform

**Splunk Key Components**:
1. Web interface
2. Search/Splunk Processing Language (SPL)
3. Apps and Add-ons
4. Knowledge Objects