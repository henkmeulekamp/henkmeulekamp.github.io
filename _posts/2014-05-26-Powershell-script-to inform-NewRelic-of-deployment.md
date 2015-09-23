---
layout: post
title: Powershell script to inform NewRelic of deployment
---

For our current script based deployment process we wanted to automaticly inform 
Newrelic of the deployment. Newrelic will then make the change in performance and 
resource usage metrics visible for that deployment, which is a really cool feature.
   
Our current production deployment scripts are batch file based.
The Newrelic API deployment call requires a HTTP POST with custom HTTP authorization header, 
so options are limited to make something simple work, which can be changed on the fly if needed. 
I settled for powershell, which I still dislike in general, but a great fit for this scenario. 
  
Setting up Newrelic deployment notifications via their API can be done in few simple steps:    
- Get my powershell from github/gist: (https://gist.github.com/henkmeulekamp/78ac923abad62c62adaa)  
- Setup Newrelic to allow API calls on your account  
- Get your NewRelic API Key  
- Get Application ID and name, within newrelic click on applications, then on the application name; The app id is the last number in the url  
- Then run by:  
    - Put those 3 in the script in the first three param value, then run script by executing:   
    - Powershell.exe -executionpolicy remotesigned -File newrelicdeploy.ps1  
- OR  
    - Set them runtime by calling the script as   
    - Powershell.exe -executionpolicy remotesigned -File newrelicdeploy.ps1 -appname yourAppName -appid yourAppId -apikey yourapiKey  
  
Thats all!
 
Reference, the powershell script:  
  
```powershell
  
param (
    [string]$appname = "your-newrelic-appname",
    [string]$appid = "your-newrelic-appid",
    [string]$apiKey = "your-newrelic-api-key"
 )

function Execute-HTTPPostCommand() {
    param(
        [string] $target = $null,
	[string] $postParam,
	[string] $key
    )
    $webRequest = [System.Net.WebRequest]::Create($target)
    $PostStr = [System.Text.Encoding]::UTF8.GetBytes($postParam)
    $webrequest.ContentLength = $PostStr.Length
    $webRequest.ServicePoint.Expect100Continue = $false
    $webRequest.Headers.Add("x-api-key", $key);
    $webRequest.Method = "POST"
	  
    $requestStream = $webRequest.GetRequestStream()
    $requestStream.Write($PostStr, 0,$PostStr.length)
    $requestStream.Close()

	[System.Net.WebResponse] $resp = $webRequest.GetResponse();
	#response check
	if ([int]$resp.StatusCode -eq 201) {
		Write-Host "NewRelic Deploy API called succeeded."
		$rs = $resp.GetResponseStream();
	    [System.IO.StreamReader] $sr = New-Object System.IO.StreamReader -argumentList $rs;
	    [string] $results = $sr.ReadToEnd();
	    return $results;
	} else {
		Write-Host "NewRelic Deploy API called failed."
		Write-Host $resp.StatusCode.ToString() + " " $resp.StatusDescription		
	}
	return "Failed";
}

```