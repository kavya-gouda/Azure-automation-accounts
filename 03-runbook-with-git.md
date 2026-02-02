# Manage Azure Automation Runbooks with Git Source Control

<img width="582" height="360" alt="image" src="https://github.com/user-attachments/assets/9f497935-15c3-4459-b668-9994fa6c95a2" />

## Auto sync
- auto Sync will not work with an automation account that uses Private Endpoint
- Use a manual sync with private endpoints
To follow Along

- Github account
- Azure Automation account
## instruction
1. if you are using devops, make sure third party application by oauth is enabled
<img width="1910" height="996" alt="image" src="https://github.com/user-attachments/assets/eb2007c1-4745-4eb4-a95b-4577995fc208" />

2. this automation will start the VM based on tag value, to make it work we need to give permision to azure account managed identity to right to start the VM permision.
   in order to do that, go to subscription, -> Access Control(IAM) -> + Add role assignement -> search "virtual machine Contributor" ->
   Memebers -> "search for Managed Identity" -> Review and Assign
3.  we need to add one more permision to Managed Identity rights to modify the automation account, specially update the runbook
   in order to do that, go to Azure automation account -> Access Control(IAM) -> + Add role assignement -> search "contributor" ->
    Membders -> Search for the Managed Identity -> review and assign
4. create repo in ADO    
5. Configure source control -> Go to automation account and under Account settings -> click on Source control -> click on add
   fill the source control summery
   Source control name:
   Source control Type:
   Azure Automation needs your permission to access your account:
   Repository:
   Branch:
   Folder Path
   Auto sync:
   Publish Runbook:
   <img width="1908" height="853" alt="image" src="https://github.com/user-attachments/assets/a377ee74-8103-4350-bcf8-baa83ed46722" />

   click save
6. clone the selected repo
   create a file "startVMbyTag.ps1
```
# Ensures you do not inherit an AzContext in your runbook
Disable-AzContextAutoSave -Scope Process

# Connect to Azure with system-assigned managed identity
$AzureContext = (Connect-AzAccount -Identity).context

# Set and store context for VMs with specific tag
$vms = Get-AzVM | Where-Object { $_.Tags['LabGroup'] -eq 'autostart' }

# Loop through and start shut down VMs
foreach ($vm in $vms) {
    # Retrieve the power state status
    $vmStatus = (Get-AzVM -Name $vm.Name -ResourceGroupName $vm.ResourceGroupName -Status).Statuses[1].Code
    
    if ($vmStatus -ne 'PowerState/running') {
       Write-Output "Starting VM: $($vm.Name)"
       Start-AzVM -Name $vm.Name -ResourceGroupName $vm.ResourceGroupName -NoWait
    }
}

```
   commit the change and push code to repo
   
7.  once pushed go to automation account, -> jobs -> here you can see the job which starts the sync, it may take few minutes
8.  once synced go to Runbooks --> you will see runbooks, with New status. you can test it and publish

9.  test and publish runbook enabled feature
