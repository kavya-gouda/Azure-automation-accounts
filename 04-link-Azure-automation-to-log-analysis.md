at some point we may decide to link Azure Automation Account to log analytics workspace. but there is not direct way to do it

<img width="1356" height="847" alt="image" src="https://github.com/user-attachments/assets/945a2be2-b2c5-4bd7-a7e2-9a4978f235a2" />

why we need it?

we want to enable a solution for azure automation, that requires the workspace. which include, update management, change tracking, start/stop VM solution. the process of enabling any of these requires log analytics workspace
we can send job, automation event data diagnostic information to analytics, this doesn't require linked workspace
log analytics workspace can only linked to one automation account and vice verse.

both has to be in same region except for eastus and

how to link?
1.  create a Log Analytics Workspace in the same region as automation account
2.  Go to automation account -> configuration management
    we can link Log analytics workspace under Configuration management -> inventory, change tracking, and update management
3. go to inventory and enable it
4. now if you go to linked workspace, you can see the our linked log analytics workspace
5. go to diagnostics settings option, edit,
   this is where we will send our audit, job and other diagnotics data in to log analytics workspace

test:
1.  create sample runbook, and publish
2.  go to log analytics -> General -> logs -> it may take 15 minutes
run the query
```
AzureDiagnostics | where ResourceProvider == "MICROSOFT.AUTOMATION"
```
4.  


