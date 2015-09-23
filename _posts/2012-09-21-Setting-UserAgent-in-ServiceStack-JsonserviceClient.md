---
layout: post
title: Setting UserAgent in ServiceStack JsonServiceClient
---
  
Quick one, ran into an issue with one of our services which require a non 
empty UserAgent header and wanted to use the 
`ServiceStack.ServiceClient.Web.JsonServiceClient` from Servicestack.  
  
Was almost going to implement it myself in the ServiceClientBase class in Servicestack and push my first pull request. But going through the code there was already an extension point, the HttpWebRequestFilter (there is an HttpWebResponseFilter also).
You can setup an action there which will be called before the request is done and gives you access to the HttpWebRequest instance.  
  
I'm using it for setting the UserAgent, but basically you can set any header (even setup the authentication headers):  
  
{% highlight c# %}  
var client = new JsonServiceClient

{
       LocalHttpWebRequestFilter = request => request.UserAgent = "MyUserAgent"
};
{% highlight C# %}  
  
Love servicestack, every time you think you found a problem there is already an extension point..
  