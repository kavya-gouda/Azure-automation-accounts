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
- 
