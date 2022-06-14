# Azure Arc-enabled-servers Security Foundation

This article focuses Azure Arc-enabled servers security foundations about identity and access and network security baseline with enterprise scale landing zone recommendations. 

	1- Use service principal to onboard servers to Azure Arc
	
An Azure service principal is an identity created for use with applications, hosted services, and automated tools to access Azure resources. This access is restricted by the roles assigned to the service principal, giving you control over which resources can be accessed and at which level.

First you need to decide how many service principal account you need o onboard servers. That's based on operational responsibility and ownership. Service principal method can be used instead of your privileged identity. 

Apps & service principals in Azure AD - Microsoft Entra | Microsoft Docs

	2- Use managed identity to access other Azure resources
	
Managed identities provide an identity for applications to use when connecting to resources that support Azure Active Directory (Azure AD) authentication. You can access Azure resource from your applications which run on your servers with managed identity. You should use

Authenticate against Azure resources with Azure Arc-enabled servers - Azure Arc | Microsoft Docs

	3- Consider required privileges - RBAC

You should consider least required privileges to onboard servers with Arc, deploy extensions and manage machines to users and groups. 

You should limit the user's privileges with Azure Connected Machine Onboarding role just for onboarding the machines to Azure. And you should use Azure Connected Machine Resource Administrator role to managed the machine all lifecycle.

You should review the Identity and Access control overview for full details: Security overview - Azure Arc | Microsoft Docs

![image](https://user-images.githubusercontent.com/9195953/173076471-18819c1a-0dd5-4c39-8750-ba679631c9d5.png)



	4- Consider Azure Private Link for connectivity 

You can connect your machines to Azure directly with Azure public endpoints ( optionally behind a firewall/proxy server) using HTTPs protocol . In this option you should configure your internet access network rules. 

Other option is connect Azure with Private Link. That option makes connections without internet /public network connectivity and allows you to securely link Azure PaaS services to your virtual network using private end endpoints. So, you can keep all traffic inside Microsoft backbone. 

For more information What is Azure Private Link? | Microsoft Docs

![image](https://user-images.githubusercontent.com/9195953/173076491-44d081df-cd60-4309-a738-b577b8d7002b.png)



	5- Use TLS version 1.2

Configure your machine to use TLS 1.2 because older versions aren't recommended due to know vulnerabilities.


	6- Encrypt onboarded server's disk to prevent offline attacks

An onboarded server with Azure Arc, a private key stored in the OS disk and agent uses that key for communication with Azure. If private key stolen, this key can be used on another server to communicate with the service and act as original server and get access to "system assigned identity" and any resource with that identity.  Hereby, we strongly recommend the use of full disk encryption on the operating system volume of your server.

For more information: Security overview - Azure Arc | Microsoft Docs

	7- Enable Guest Configuration

Azure Policy help you to audit and configure setting from Azure and you can enable and disable this functionality by running the following configuration. When you disabled that configuration on server, Azure will report assigned Guest Configuration policies as non-compliant.

azcmagent config set guestconfiguration.enabled true

	8- Block Custom Script Extension

You can allow or block any extension on the server. Extension managed handle all operations against the allowlist or blocklist. You shouldn't include Custom Script Extension in the allowlist to prevent execution of arbitrary scripts. 

For more information: Security overview - Azure Arc | Microsoft Docs

You should review the following guides :

[Ready methodology for hybrid and multicloud strategy - Cloud Adoption Framework | Microsoft Docs](https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/hybrid/ready)

[Azure identity and access management design area - Cloud Adoption Framework | Microsoft Docs](https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/hybrid/ready)
	
