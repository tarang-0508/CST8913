
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


##Section-2

Migration Plan

1) Web Application
The assessment of existing dependencies should lead to monolithic code restructuring when required.

Implement the test environment using selected PaaS platform.

The migration of the web application follows up with performance testing procedures.

Switch traffic to the new cloud environment via DNS updates.

Discontinue using on-prem servers after the migration reaches stability.


2) Database 

Migrate the database from its current hosting to an Infrastructure as a Service-based Microsoft SQL Server setup.

Enhancing database queries and index performance will deliver cloud system speed.

The solution requires migration towards PaaS Database Service through platforms like AWS RDS or Azure SQL or their equivalents.

The system must undergo testing of connectivity between applications while resolving all encountered compatibility problems.

End operation of the IaaS SQL instance following a stable migration performs successfully.


3) File Storage

The team needs to evaluate storage demand alongside performance standards.

Cloud object storage implementation accompanied by permission setup procedures.

Cloud migration tools including AWS S3 Transfer and Azure Storage Migration should be used to move data.

The application needs reconfigured settings that point to the new storage resources.

The retirement of local storage requires confirmation of access and performance before it can proceed.


4)  Networking

Design hybrid cloud network architecture.

Conduct a setup of VPC, VPN or Direct Connect solutions for establishing secure network connections.

Establish security configurations for firewalls in addition to Web application firewalls and Distributed Denial of Service defense systems.

Both the performance of the network and strategies for failover need to be tested.

Logs should be monitored alongside security rules optimization.


5) Email Services

Evaluate SaaS providers and select a service (AWS SES, Microsoft 365, etc.).

Migrate email data and configure domains.

Update SMTP settings in applications.

Test email delivery and security policies.

Decommission on-prem email servers.

# Cloud Migration

| On-Prem Component  | Migration Strategy                                | Cloud Offering                                    | Reasoning |
|--------------------|--------------------------------------------------|--------------------------------------------------|-----------|
| **Web Application** | Refactor to PaaS | PaaS (AWS Elastic Beanstalk, Azure App Service) | Reduces operational overhead, enables auto-scaling, and improves deployment efficiency. |
| **Database** | Lift-and-Shift to IaaS, then migrate to PaaS | IaaS (AWS EC2 + SQL Server, Azure VMs + SQL) → PaaS (AWS RDS, Azure SQL) | Ensures minimal downtime initially, then moves to PaaS for better scalability. |
| **File Storage** | Migrate to Object Storage | PaaS (Amazon S3, Azure Blob Storage) | Reduces infrastructure management and improves availability. |
| **Networking** | Implement Cloud-Native Networking | IaaS (AWS VPC, Azure Virtual Network) | Ensures security, redundancy, and hybrid connectivity. |
| **Email Services** | Move to SaaS | SaaS (AWS SES, SendGrid, Microsoft 365) | Reduces management complexity and provides built-in security & compliance. |

Hybrid Migration Plan

1) Web Application

The first step deploys the web app through cloud VMs (Infrastructure as a Service) for ensuring system stability.

The second phase focuses on refractometer towards PaaS systems which includes AWS Elastic Beanstalk and Azure App Service.

2) Database 

The initial step entails migrating SQL Server into a virtual machine using cloud infrastructure as a service (IaaS) while maintaining database synchronization between on-premises and cloud databases.

The database will transition from cloud VM (IaaS) in Phase 1 to PaaS solutions like AWS RDS and Azure SQL in Phase 2 for automated management control.

3) File Storage

The first phase involves transferring enumerate files to virtual machine storage in the cloud through Infrastructure as a Service (IaaS).

The business should transition to PaaS platforms such as AWS S3 and Azure Blob solutions for scalability purposes after Phase 1 completes.

4)  Networking

The first phase establishes either Hybrid VPN or Direct Connect to manage the transition successfully.

Moving operations to cloud-native networking infrastructure includes VPC and security groups with firewalls should be implemented during Phase 2.

5) Email Services

The first phase involves synchronization of on-site mail servers to operate through a cloud-based relay.

SaaS migration to Microsoft 365 or Google Workspace will become the complete operational strategy.


## Hybrid Migration Strategy per Component

| Component       | Phase 1 (Temporary - Hybrid) | Phase 2 (Final - Cloud) | Migration Strategy |
|---------------|------------------------------|--------------------------|---------------------|
| **Web Application** | IaaS (VMs in Cloud) | PaaS (App Service) | **Replatform** (Hybrid IaaS → PaaS) |
| **Database** | IaaS (SQL on VM) | PaaS (Managed SQL) | **Rehost** (Hybrid SQL replication) |
| **File Storage** | Hybrid Storage (VM-based) | PaaS (S3, Blob Storage) | **Replatform** |
| **Networking** | Hybrid VPN / Direct Connect | Cloud-Native (VPC, WAF) | **Re-architect** |
| **Email Service** | Hybrid Email Sync | SaaS (Microsoft 365, Google Workspace) | **Replace** |






