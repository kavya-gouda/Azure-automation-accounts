# Azure-automation-accounts

## what is Azure automation accounts?
Azure automation account is a cloud based  automation service that allows you to automate repitative tasks in your azure and on-prem environments. Think of it as your personal assistent that works 24/7

with Azure automation, you can:

- Run powershell or python scripts automatically
- Schedule jobs like VM start/stop, resource cleanup, or updates
- Manage configuration, inventory, and updates for VM's
- Integrate with logic apps, runbooks, and hybrid workers
## features:
process automation
Configuration Management
Shared Resources

## use cases:

- Auto shutdown VM's at night to save cost
- Automatically start VM's before office hours
- Schedule patching for windows/Linux VM's
- Cleanup unused resources daily
- Automate backup or snapshot creation
- Connect to on-prem servers with Hybrid runbook worker

## other options
- Azure Functions : Event Driven serverless automation tool
- Azure Logic apps : Graphical user interface to build workflows and process automation
## Managed Identity
# Managed Identity
Azure automayion account have Managed identity to connect and work with other resources

- System Assigned: Created with the Azure Automation account and bound to the lifecycle of the account
  <img width="587" height="337" alt="image" src="https://github.com/user-attachments/assets/ceb15323-467d-44d3-a1d2-dc346703fb8d" />
- User Assigned: Created independently of the Azure Automation account, use by multiple automation accounts or other Azure resources
  <img width="577" height="351" alt="image" src="https://github.com/user-attachments/assets/4cd1ac56-cb2e-4f6f-b94e-5003f3ac5d6f" />

----
# creation 

# review the system assigned Managed Identity

1. Go to Azure Active Directory and Enterprise applications
   <img width="942" height="851" alt="image" src="https://github.com/user-attachments/assets/62e78bf7-e002-4ab0-9fe8-74e3541fbf45" />

2. change the application type to Managed Identity
<img width="907" height="735" alt="image" src="https://github.com/user-attachments/assets/3bdbb5d6-b061-42a3-9244-e0637f972850" />
3. you can see our automation account
   <img width="920" height="910" alt="image" src="https://github.com/user-attachments/assets/4a33c2ba-b70f-40e4-8531-2e37816c76a7" />
4. go to role and administrators
   <img width="1136" height="763" alt="image" src="https://github.com/user-attachments/assets/00b60343-b1f5-4405-bc5b-3632e923f542" />
   these roles are at the AD scope , if we want to interact with resources in subscription, we need to give access to that resource
5. Go to resource group of automation account, Access Control(IAM)
   <img width="1072" height="917" alt="image" src="https://github.com/user-attachments/assets/ddece55e-9723-4731-bed0-6142b86af401" />
    
6. + Add role assignement, select reader,
  <img width="1068" height="910" alt="image" src="https://github.com/user-attachments/assets/2c62a5c6-f5c1-4e4e-874d-e64d304e3e31" />
7. select a member and search for Managed Identity of the automation account
   <img width="1071" height="945" alt="image" src="https://github.com/user-attachments/assets/4e6a14ab-c4f7-424d-9d5a-c5807e82f70e" />

----
# Create first Runbook
