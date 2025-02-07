Q-1: A solution diagram showing the target architecture with load balancers and multi-region VMs.

Ans: A multi-region cloud deployment system with load balancing capabilities built for failover purposes presents the target architecture.

The application moves to a cloud-based multi-region architecture to provide high availability, fault tolerance, and scalability. The solution uses multiple strategies, including load balancing and database replication, along with automation, which helps reduce downtime and guarantee system performance.

Key Components of the Architecture:

Global Load Balancer
The Global Load Balancer forwards traffic from users to the cloud region offering peak availability with minimal latency.

Primary Region
Traffic distribution through LB-A establishes a connection with multiple WebServer VMs across the network.
The application data is stored in the primary SQL database, which operates under SQLVM-A.
The database stores static assets as objects in a cloud-based storage solution.

Secondary Region
The backup WebServers are reached through the second load balancer, named LB-B.
SQLVM-B manages a duplicate read database for failover support.

Database Replication
Ensures real-time synchronization between the primary and secondary databases.

Failover Mechanism
The system sends traffic to Region B when Region A encounters outages.
After an outage, the Region B database replication automatically takes over as the primary to ensure data consistency.

         ```mermaid graph TD;
    A[Global Load Balancer] -->|Traffic Distribution| B[Primary Region]
    A -->|Traffic Distribution| C[Secondary Region]
    B --> D[Regional Load Balancer - Primary]
    C --> E[Regional Load Balancer - Secondary]
    D --> F[Web Server]
    E --> G[Web Server]
    F --> H[SQL VM - Primary]
    G --> I[SQL VM - Secondary]
    H -- Replication --> I
    I -- Failover --> H



Q-2: A description of the target architecture highlighting redundancy and failover mechanisms.

Ans: Multi-Region Cloud Architecture with Redundancy and Failover Mechanisms.

Cloud computing platforms today prioritize high availability, scalability, and fault tolerance to sustain business operations. This document presents a multi-region cloud architectural design that combines redundancy features with failover components to ensure uninterrupted service availability.

1) Target Architecture Overview:

The proposed model implements two cloud zones (Primary and Secondary) that contain web service servers and database systems. A Global Load Balancer functions to send users to the most available region with minimal latency. The Regional Load Balancer within each region distributes traffic between various WebServers to process requests efficiently.

The implementation includes the primary SQLVM-A running in the primary region and the disaster recovery secondary SQLVM-B operating in the secondary region.

2) Redundancy Mechanisms:

The following redundancy systems enhance system resilience:

Multi-Region Deployment: Spreading the system across two separate cloud regions ensures no service interruptions due to regional failures.
Global Load Balancer (GLB): The GLB connects users to the most efficient region for smooth service access.
Regional Load Balancer: A local load balancer divides incoming traffic between multiple WebServerVMs, preventing overload of a single server instance.
Multiple WebServerVMs: Each cloud region has multiple WebServerVMs to maintain service availability when one server fails.
3) Failover Mechanisms:

There are three key failover mechanisms to handle failures effectively:

(i) Database Replication & Automatic Failover:
Database replication technologies maintain constant data replication between the Primary SQLVM (Region A) and Secondary SQLVM (Region B). When failures occur in Region A, the secondary database automatically takes over as the primary to maintain data availability.

(ii) Traffic Rerouting:
The Global Load Balancer detects failures and automatically reroutes traffic to operational regions. The regional load balancers within the secondary region then direct incoming traffic to operational WebServerVMs.

(iii) Automated Health Monitoring:
The continuous monitoring process verifies the operational status of web servers and databases. When a failure is detected, traffic is redirected to operational servers within the nearest healthy region.

4) Benefits of the Architecture:

This framework provides various benefits to users:

The redundant infrastructure ensures brief interruptions in service access.
Replicated databases and multiple web servers act as fault tolerance mechanisms to prevent service outages.
Load balancers optimize traffic distribution for handling scalability requirements.
The secondary region serves as a disaster recovery site, ensuring operational continuity in case of failure.
The Global Load Balancer handles incoming traffic before regional load balancers distribute requests to multiple WebServerVM instances. Automatic traffic rerouting ensures that the secondary database takes control, minimizing downtime and ensuring continuous business operations.


Q-3: The steps of migration, including:

Replication of virtual machines across regions.
Configuration of load balancers.
Implementation of database replication and failover.
Ans: Smooth migration of the two-VM application (WebServerVM and SQLVM) into a multi-region cloud architecture requires specific steps that ensure availability and reduce downtime. Virtual machine replication, load balancer setup, and database replication with failover mechanisms form the core steps of the migration process.

1) Replication of Virtual Machines Across Regions:

Virtual machines (VMs) must replicate across multiple cloud regions to establish redundancy and failover capabilities.

First, assess the existing configurations, dependencies, and performance requirements of WebServerVM and SQLVM.
Implement the infrastructure in the secondary region.
The secondary cloud region should be set up with identical configurations as the existing virtual machines.
Network connectivity and security configurations must match those in the primary region.
Migrate WebServerVM Instances:

Use image-based snapshots or live migration tools to duplicate WebServerVM instances and deploy them in the secondary region.
Deploy multiple WebServerVMs in each geographical region (primary and secondary).
Migrate SQLVM (Database Server):

Add a second SQLVM in the failover zone, ensuring matching database engine configurations.
Synchronize the primary and secondary databases through replication.
2) Configuration of Load Balancers:

The load balancing setup should be done both globally and regionally to ensure efficient traffic distribution and high availability.

Global Load Balancer (GLB) Configuration:
Install the Global Load Balancer to distribute traffic between the two cloud regions. Use geo-location routing to direct users to the closest, healthiest region. The failover policy automatically redirects traffic to the operational backup location when the primary region fails.

Regional Load Balancers:
Implement Regional Load Balancers in each cloud region. Use the load balancer to distribute traffic among multiple WebServerVMs and automatically perform health checks. When failures are detected, requests are redirected accordingly.

3) Implementation of Database Replication and Failover:

Data availability requires proper database replication between the Primary SQLVM and Secondary SQLVM.

Select a replication method based on the database type and configure either synchronous or asynchronous replication for data consistency.

Configure Primary and Secondary Databases:
Set up the Primary SQLVM to send real-time data replication to the Secondary SQLVM, ensuring identical security and encryption protocols across both regions.

Enable Automatic Failover:
Implement failover mechanisms like database clustering, SQL Server's Always On Availability Groups, or MySQL/PostgreSQL Read Replica Promotion. When a failure occurs, promote the secondary database to the primary to minimize downtime.

Test and Validate Failover:
A test of failed primary database operations must show the secondary database automatically takes control of the operation.
The system needs to maintain application read/write processes without any data losses occurring.
