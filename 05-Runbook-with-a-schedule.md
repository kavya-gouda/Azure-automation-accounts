# schedule and apply it to runbook
schedule are shared resources, we can create them and run them with other runbooks
## creation
go to automation account -> shared resources -> schedule -> Add a schedule -> give below details

name: weekday at 7:00AM
Description:
Starts : 
TimeZone: 
Recurrence:

minimum reoccuring is one hour, if you need to run it frequently, check for azure function

once created, link it to a runbook

go to runbook -> select the runbook -> resources -> add schedule -> select the created schedule, and link it

if you go back to automation account -> schedule -> botton you can see which runbook it is linked


