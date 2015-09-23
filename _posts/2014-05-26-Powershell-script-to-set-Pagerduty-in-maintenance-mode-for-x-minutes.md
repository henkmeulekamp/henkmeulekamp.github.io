---
layout: post
title: Powershell script to set Pagerduty in maintenance mode for x minutes via API
---
  
After the previous quick post on notifying NewRelic of a deployment using a powershell script I setup a second script to inform Pagerduty to set certain alerting services into maintenance mode. The idea is the same; an easy on the fly changeable powershell script which can be executed from batch deploy scripts and will perform an HTTP POST to Pagerduty REST Api using some command-line parameters.
  

The steps:  
1. Get the powershell script from github gist (https://gist.github.com/henkmeulekamp/3441f937caf991d6500b)
2. Get your pagerduty API token, which is [described here](https://support.pagerduty.com/hc/en-us/articles/202829310-Generating-an-API-Key)
3. Get a requersterId, which is a userId. You can find these by going into your Pagerduty account and open a user from the user tab. The requesterId is the last part of the path after users/
4. Open the Pagerduty services from the services tab. The serviceIds are the last part of the path after after services. You need to get the id from each service which need to be set to maintenance mode.
5. Determine your needed maintenance window in minutes, from the moment your script is executed.
6. Set all these param values in the first param script block of the script.
7. The previous step is optional when you want to run the script using command-line params.
8. Then run script by:
    - `Powershell.exe -executionpolicy remotesigned -File pagerduty-maintenance.ps1`
    - OR
    - `Powershell.exe -executionpolicy remotesigned -File pagerduty-maintenance.ps1 -minutes 3 -requesterId ABC1234 -apiKey ABC123 -description "New version deployed" -serviceIDs "'serviceId1', 'serviceId2', 'serviceId..'"`
  
Thats all!
  