at some point we may decide to link Azure Automation Account to log analytics workspace. but there is not direct way to do it

<img width="1356" height="847" alt="image" src="https://github.com/user-attachments/assets/945a2be2-b2c5-4bd7-a7e2-9a4978f235a2" />

why we need it?

we want to enable a solution for azure automation, that requires the workspace. which include, update management, change tracking, start/stop VM solution. the process of enabling any of these requires log analytics workspace
we can send job, automation event data diagnostic information to analytics, this doesn't require linked workspace
log analytics workspace can only linked to one automation account and vice verse.

