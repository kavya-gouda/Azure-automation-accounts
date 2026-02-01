# Creation

click on create resource and search for automation account
<img width="1890" height="900" alt="image" src="https://github.com/user-attachments/assets/eb255683-5bc7-4722-9749-7b187a423c13" />

select automation account -> create

fill the below details
- Basics
  - Subscription
  - Resource group
 Instance Details
  - automation account namw
  - Region
 
<img width="852" height="827" alt="image" src="https://github.com/user-attachments/assets/10a76c4b-c474-4327-8549-abdd09f68cff" />

- Advanced:
  in azure eco system we can connect with other resources using Manager Identities. in Managed Identity we have 2 options
  - System assigned :  life cycle of this manager identity stays with resources
  - User assigned : mnually created, lifecycle of this identity will not be with resources
  <img width="767" height="892" alt="image" src="https://github.com/user-attachments/assets/49138075-3a11-4934-8af7-ba827a99a55a" />

- Networking:
  Network connectivity will have two option public access and private access for endpoint of the account
  <img width="812" height="912" alt="image" src="https://github.com/user-attachments/assets/151a5a1d-de73-46ea-b278-48adb7761c2f" />

- Tags:
- review and create
<img width="705" height="898" alt="image" src="https://github.com/user-attachments/assets/28232a64-2a2d-4fe4-8a2e-c6f989f715fd" />

<img width="1420" height="901" alt="image" src="https://github.com/user-attachments/assets/da750db5-2a40-453d-8f3d-bc299619e816" />

## what can we do with Automation account (capabilities)
- Process Automation
  - Runbooks: 
  - Jobs
  - Hybrid worker groups : automaate on-prem services
- Configuration Managements
  - State Configuration (DSC) : configurtion to windows VM
- Shared Resource
  - Schedule 
  - Modules : pwershell modules
  - Python packages
  - Crednetials
  - Connections :establish connection to target resources
  - certificates
  - Variables
- Related Resources
  - Linked workspace : 
  - Event Grid
  - Start/Stop VM
  - Watcher tasks
<img width="1903" height="796" alt="image" src="https://github.com/user-attachments/assets/e2d52d2c-d2f3-47a9-8c0d-9a85c353b1c8" />
