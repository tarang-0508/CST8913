
Section=1

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

