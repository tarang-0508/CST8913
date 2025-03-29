# Migration Plan – Tailwind OpenCare
- Moving the core Patient Self-Booking System of Tailwind OpenCare to Microsoft Azure serves as an essential step for better scalability and reduced operational costs alongside compliance adherence. The migration blueprint features precise procedures to accomplish a smooth transition which delivers powerful data protection and small disruptions and efficient cost reduction through Azure-native functionalities.


## 1. Discovery and Tooling Setup

## Tools to Use:
- **Azure Migrate**: Azure Migrate functions as the most suitable tool for discovering and assessing on-premises workloads before conducting a migration. Tailwind has two options with Azure Migrate Appliance either through agentless discovery to get all data or agent-based discovery to gain complete data specifics.
- **Azure Migrate App Dependency Mapping**: The analysis tool App Dependency Mapping determines the service connections in the system.
- **Azure Migrate Database Assessment**: The Database Assessment tool serves as a method to determine whether PostgreSQL database will match the Azure Database for PostgreSQL.
- **Azure Migrate Server Assessment**: Server Assessment conducts a survey of pre-existing NGINX, Node.js, PostgreSQL, Redis servers and develops migration planning.

## Data to be Collected
- **Operating system**: Log the versions of Operating System and each component including Nginx, Node.js, PostgreSQL, Redis and backup tools.
- **Hardware Information**: Acquire CPU together with memory and disk specifications from every on-premises system.
- **Network Configuration**: Obtain information about load-balancing setup with HAProxy along with firewall rules along with IP addresses and associated settings to confirm network connectivity works after migration.
- **Dependencies**: Establish the dependencies between NGINX frontend and Node.js backend services to display their clear service relations.

## Credentials and Permissions
- Identity and access management functions should use Azure Active Directory (Azure AD).
- Azure resources should have Role-Based Access Control (RBAC) setup for secure permission management across all resources.
- All credentials should be safely stored inside Azure Key Vault to manage secrets keys and certificates securely.

# 2. Assessment Planning

## Assessment Parameters to Configure in Azure Migrate

- **Performance History**: Performance metrics should be set to collect data over 30 days or more to analyze CPU usage, memory utilization and disk and network usages. The collected data will enable developers to choose the appropriateAzure resources size.
- **Sizing Strategy**: Organizations must decide whether to adjust resource sizes according to present requirements through right-sizing or dedicate surplus resources in anticipation of upcoming load surges through over-sizing.

## Target Azure Region, Compute Type, and Storage Type

- **Target Azure Region**: Select an Azure location which provides minimum latency to Tailwind OpenCare’s users (East US or North Europe).
- **Compute Type**: Organizations should implement Azure Virtual Machines with Standard D-series for generic purposes but consider using B-series if cost reduction is necessary.
- **Storage Type**: Deploy Azure Managed Disks as data storage solution by selecting either Standard SSD or Premium SSD based on performance needs for web servers, backend and database.

## Validating Assessment Results with Stakeholders

- Present the **Azure Migrate Assessment Report** to stakeholders for their evaluation.
- Application owners need to approve all sizing and configuration solutions to validate proper management of essential performance indicators.

## 3. Dependency Analysis and Optimization

## Dependency Mapping 
- Agentless Dependency Mapping helps organizations detect application dependencies through its discovery method which does not require installing agents on on-premises systems. The information about network dependencies alongside inter-service communication will be obtained by Azure Migrate from its discovery process.
- Agent-based dependency mapping serves detailed purposes since it reveals component interconnections for intricate mapping situations.

## Cleaning Dependency Data
- **Filter Known System Dependencies**: Cluster all dependencies which are non-essential or unknown elements from critical pathways (like system-level services which consist of monitoring or backup services).
- The application framework depends on the backend API while the backend API needs PostgreSQL database services to operate properly.

## key metrics
- **Criticality**: Determine which services specifically the Node.js API along with others because they represent core business components for operations.
- **User Base**: The team should establish which services require increased traffic capabilities including the frontend NGINX servers.
- **SLA**: The migration process in Azure requires performance and uptime verification to maintain SLA compliance for every service.
- **Backup Requirements**: The migration process in Azure requires performance and uptime verification to maintain SLA compliance for every service.

## 4. Server Grouping and Migration Waves

## Logical Server Groupings
- **Frontend**: Two NGINX webservers.
- **Backend**: Two Node.js API servers.
- **Database**: PostgreSQL database.
- **Cache server**: Redis instance separately.

## Migration Waves
- **Wave 1**: Start by moving the NGINX web servers since they possess low complexity while having minimal dependencies.
- **Wave 2**: The Node.js API servers must be migrated to Azure connectivity after reestablishing their links with both PostgreSQL database and Redis instances.
- **Wave 3**: Any migration of PostgreSQL and Redis instances must wait until the end of the process since both play an essential role in maintaining application functionality.

## Precautions
- The Azure administrator needs to update firewall rules to ensure safe networking between frontend and backend systems.
- Deploying new load balancers as part of the migration process requires both Azure Load Balancer as well as Application Gateway configuration.
- After migration check that IP addresses along with DNS records have been correctly updated to prevent operational issues.

## 5. Migration Plan Documentation 

### Step 1- Preparation
- You need to establish Azure Migrate and its discovery tools to obtain a server inventory.
- The implementation of Azure Key Vault will manage secrets and credentials within the system.
- The preparation of Azure Networking includes configuring both Virtual Networks and Subnets and establishing a VPN Gateway if necessary.

### Step 2- NGINX Web Servers
- Establish Azure Virtual Machines as hosts for the NGINX web servers.
- The transfer of NGINX configuration as well as static content needs to be performed to Azure Virtual Machines.
- The implementation of Azure Load Balancer should handle traffic distribution among the NGINX servers.
- The DNS needs modification to use the new Azure load balancer as its destination.

### Step 3- Node.js API Servers
- Establish Azure Virtual Machines that will run the Node.js backend software.
- The deployment of the Node.js application to Azure needs configuration to connect with Azure Database for PostgreSQL and Redis.
- Check whether the network connections work between your frontend component running on NGINX and your backend component operating on Node.js application.

### Step 4- PostgreSQL Database and Redis
- Migration of PostgreSQL database to Azure Database for PostgreSQL will be performed.
- The deployment must establish an Azure Cache for Redis implementation as part of caching functions.
- PostgreSQL requires daily backup implementation as a part of backup strategy deployment.


### Final Step- Validation
- Execute a comprehensive test for the complete application system to validate functional capabilities.
- The complete system requires testing with post-migration validation for both load performance evaluation and security assessments.
- Test the operational status of the daily backup system.

## DNS and Storage Replication
- You need to create DNS records which point to Azure resources.
- The migration requires Azure Site Recovery or Azure Blob Storage replication for data consistency if applicable.

## Role of Application Owners:
- Before starting migration: Application owners should test their systems with pre-migration simulations as well as through Azure application deployment testing.
- Application owners should verify application functionality in Azure since they need to monitor performance during the first stages after system migration.

--- 








