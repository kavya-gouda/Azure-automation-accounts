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
1.  go to Automation Account and click on Create a runbook
  <img width="1621" height="891" alt="image" src="https://github.com/user-attachments/assets/926c6855-89d2-489f-b208-aac212b051d6" />
  <img width="863" height="912" alt="image" src="https://github.com/user-attachments/assets/4de61933-fc6b-4e35-8711-a71184407fa4" />

2. fill the details and click on create
     <img width="790" height="903" alt="image" src="https://github.com/user-attachments/assets/16b86986-4e13-414b-9273-75901a0f59a6" />
3. Edit the Runbook in editor
   <img width="1067" height="942" alt="image" src="https://github.com/user-attachments/assets/bc2cfc0d-ed65-407d-8d7b-d809295b21ae" />
4.  Add below powershell command to check the version
```
# Ensure you do not inherit an AzContext in your Runbook
Disable-AzContextAutosave -Scope Process

# Connect to Azure with system-assigned identity
$AzureContext = (Connect-AzAccount -Identity).context

# Set and store context
$AzureContext = Set-AzContext -SubscriptionName $AzureContext.Subscription -DefaultProfile $AzureContext

# Corrected line without the $ symbol
Get-AzAutomationAccount -ResourceGroupName "automation-account" -Name "account-test-lab"
```
5. click save and go to test pane
<img width="1880" height="888" alt="image" src="https://github.com/user-attachments/assets/6c77574d-a11b-42c4-82f1-a01d5d88e7c9" />
Test doesn't count as jobs
6.  if it all looks good, publish it
<img width="1547" height="940" alt="image" src="https://github.com/user-attachments/assets/a2cf7e50-6aab-4622-a2e8-9b14713dacba" />

7.  go to runbook click on start
   <img width="1686" height="881" alt="image" src="https://github.com/user-attachments/assets/f8802c8a-bbb1-4169-a287-c0813b3aedda" />

9.  Once the status is completed. you can check output/Errors/Warnings and many more
    <img width="1903" height="946" alt="image" src="https://github.com/user-attachments/assets/4e1cac39-ced9-444f-ba28-c8617b0dae0a" />

11.  
