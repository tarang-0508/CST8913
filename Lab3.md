
#Section=1

[Internet]  
│  
├───[Firewall] (Active/Passive HA)  
│   │  
│   ├───[Web Tier]  
│   │   ├───[Load Balancer]  
│   │   ├───[VM Cluster: Web Servers] 
│   │  
│   ├───[Database Tier]  
│   │   ├───[SQL Server](Active Node)  
│   │   └───[Backup Server]  
│   │  
│   ├───[Storage Tier]    
│   │   └───[Object Storage Gateway] 
│   │  
│   ├───[Email Services]  
│   │   ├───[Mail Server Cluster]   
│   │   └───[Spam/AV Filter]  
│   │  
│   ├───[Networking]  
│   │   ├───[Core Switches] (Cisco Catalyst, stacked for redundancy)   
│   │   └───[IDPS]  
│   │  
│   └───[Management & Monitoring]  
│       ├───[Hypervisor Hosts] (VMware vSphere/Hyper-V Cluster)  
│       ├───[Monitoring] (Prometheus + Grafana, Nagios)  
│  
└───[DMZ] (Optional for public-facing services)


# Cloud Migration Strategy

| **On-Prem Component**                         | **Cloud Equivalent**                            | **Cloud Offering (PaaS, IaaS, SaaS)**                         |
|-----------------------------------------------|-------------------------------------------------|---------------------------------------------------------------|
| **Firewall (Active/Passive HA)**              | Cloud-based firewall and DDoS protection        | **IaaS (Azure Firewall, AWS WAF, Cloud Armor)**               |
| **Load Balancer**                             | Cloud-native load balancing                     | **PaaS (AWS ALB, Azure Load Balancer, GCP LB)**               |
| **VM Cluster (Web Servers)**                  | Managed containerized services                  | **PaaS (AWS Elastic Beanstalk, Azure App Service)**           |
| **SQL Server (Active/Backup)**                | Managed database services                       | **PaaS (AWS RDS, Azure SQL Database, Cloud SQL)**             |
| **Object Storage Gateway**                    | Cloud object storage                            | **IaaS (Amazon S3, Azure Blob, Google Cloud Storage)**        |
| **Mail Server Cluster**                       | Cloud-based email service                       | **SaaS (AWS SES, SendGrid, Microsoft 365, Google Workspace)** |
| **Spam/AV Filter**                            | Cloud-native email security                     | **SaaS (Proofpoint, Microsoft Defender, Mimecast)**           |
| **Core Switches (Cisco Catalyst)**            | Cloud-based networking & hybrid connectivity    | **IaaS (AWS Direct Connect,Azure ExpressRoute,Interconnect)** |
| **IDPS (Intrusion Detection & Prevention)**   | Managed security services                       | **IaaS (AWS GuardDuty, Azure Security Center)**               |
| **Hypervisor Hosts (VMware/Hyper-V)**         | Virtual machine instances                       | **IaaS (AWS EC2, Azure VMs, Google Compute Engine)**          |
| **Monitoring (Prometheus/Grafana/Nagios)**    | Cloud-based monitoring                          | **PaaS (AWS CloudWatch, Azure Monitor,GCP Operations Suite)** |
| **DMZ (Public-facing services)**              | Cloud-native WAF and CDN                        | **PaaS (AWS CloudFront, Azure Front Door, Google Cloud CDN)** |


