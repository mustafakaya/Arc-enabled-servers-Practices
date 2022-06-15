# Monitor Arc-Enabled-Servers

Azure Arc helps you to manage virtual machines or physical servers outside of Azure like an Azure resource. You can easily enable and monitor your machines with enabling that Azure Arc. After enable a server with Azure Arc, you can use Azure native services for your non-Azure resource.  Azure Monitor is umbrella service to collect, analyze and act on telemetry data from Azure and non-Azure services. We use Azure Monitor for full observability at application, infrastructure and network level. 

In this article, I'll focus on how we can enable Azure Monitor easily for Arc-enabled-servers and all options to watch your Arc-enabled servers.

There're different options to monitor your Arc-enabled-servers from Azure. 

1- Insights with Microsoft Monitoring Agent

First one is enable Insights directly for your server from portal. That method installs Microsoft Monitoring Agent extension on your server and collect data to Log Analytics Workspaces.

![image](https://user-images.githubusercontent.com/9195953/173695471-8dea8558-135c-4e73-a9da-f226647916af.png)


Then you can see your server's metrics at Performance section of Insights section like below:

![image](https://user-images.githubusercontent.com/9195953/173695492-0cf8595d-0ae5-4ee9-bd06-f47b46e07f93.png)

You can see server dependencies and components under Map section:

![image](https://user-images.githubusercontent.com/9195953/173695504-304e535a-0d4d-4166-ae25-c974073f3cb7.png)


2- Azure Monitor Agent

Azure Monitor Agent is replacement of Log Analytics agent and you can use that agent for Arc-enabled servers. You can follow the below steps to install Azure Monitor Agent extension to your Arc-enabled-server. 

You can read the following guide to understand the agents and differences: Overview of the Azure monitoring agents - Azure Monitor | Microsoft Docs

	1. Assign the required role to install Azure Monitor Agent (AMA) for Arc-enabled-server

For methods other than Azure Portal, you must have the "Azure Connected Machine Resource Administrator" role assignments to install the agent:

	2. Create a data collection rule

Azure Monitor Agent uses data collection rules that defines which data sent to Azure Monitor. So, you need to create a data collection rule in the Azure Portal and then associate that rule with a Arc-enabled server. You can create one or many rule for an Arc-enabled server and you can use same rule with multiple servers. 

First you need to identify scope that's the Arc-enabled server. Also you can create private links for collecting data with creating or using an endpoint.

![image](https://user-images.githubusercontent.com/9195953/173695562-121a7901-4581-40d8-8383-43e036af6b95.png)

![image](https://user-images.githubusercontent.com/9195953/173695577-cdcfeef2-db45-4f29-ad5c-bc4992cca4a7.png)

![image](https://user-images.githubusercontent.com/9195953/173695584-c42ee33e-c1c2-4b08-aff3-4a75eb7000a1.png)

Then you need to add data source which is data to collect with agent and select a destination Log Analytics Workspace to collect data.

![image](https://user-images.githubusercontent.com/9195953/173695593-4d2446f0-110a-4c26-8647-2f722cc19ad2.png)

![image](https://user-images.githubusercontent.com/9195953/173695638-bf0cc29e-93b9-45af-98a3-93dcf230e37f.png)


3- Windows Admin Center (WAC) (Preview)

Windows Admin Center is browser-based management tool and help to you manager your Windows Servers. You can easily install Windows Admin Center extension for your Arc-enabled-servers and then monitor your servers with different perspectives.

First you need to setup WAC to your server, that installs extension to your server.   Then you can connect your Arc-enabled-servers and watch your Windows server.  You can easily see basic metrics such as CPU and you can use Performance Monitoring and Packet Monitoring tools for your server easily. 

![image](https://user-images.githubusercontent.com/9195953/173695657-4e3e4df5-e984-4626-901c-06ed42de1cbb.png)







