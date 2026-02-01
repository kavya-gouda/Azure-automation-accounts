# Azure Automation Hybrid Worker with Azure Arc enabled server

<img width="560" height="372" alt="image" src="https://github.com/user-attachments/assets/9d082c5c-a7b4-4d73-8aa0-28cbbe4f54ac" />

# Hybrid Worker Configuration
-  Required Powershell and Python modules must be added manually to the hybrid workers
-  Keep modules consistent in a worker group
-  Default system account on windows or nxautomation account on Linux
-  Custom Hybrid worker credentials do not support MFA

Runbook Worker Types

- System Worker - Used by Azure update management
- User Worker - Part of the worker group that supports runbooks outside of azure
  -  Agent-based v1 = uses the log analytics agent
  -  Extension-based v2 - uses Azure Arc to add the extension to an Arc enabled server
  
 # Connected Machine Agent for Extension Based Worker
 
  - Windows server 2022(includinig server core)
  - windows Server 2019(
  - Windows server 2016 version 1709 and 1803 (exclusion server core)
  - Windows server 2012,2012 R2
  - Debian GNU/Linux 7 and 8
  - Ubuntu 1804 and 20.04 LTS
  - SUSE Linux Enterprise Server 15, and 15.1
  - RedHat EnterPrise Linux server 7 and 8

  - 
