# Migration Plan – Tailwind OpenCare
Moving the core Patient Self-Booking System of Tailwind OpenCare to Microsoft Azure serves as an essential step for better scalability and reduced operational costs alongside compliance adherence. The migration blueprint features precise procedures to accomplish a smooth transition which delivers powerful data protection and small disruptions and efficient cost reduction through Azure-native functionalities.


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

