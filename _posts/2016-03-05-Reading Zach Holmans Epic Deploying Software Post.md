---
layout: post
title: Reading Zach Holman's Deploying Software Post
---

While reading Zach Holman's Deploying Software I decided to write-up some notes. He produced such an epic post that I probably want to go back in the future to look at some of the points again.
  
[@Holman](https://twitter.com/holman)  
[Deploying Software](https://zachholman.com/posts/deploying-software)
  
The main point of the article:  
**Make that typically-scary new release deploy as fast, boring, straightforward, and stress-free as possible.**
  
As this is just what we are trying to do, most of the points resonated with me.

# Notes
  
Everyone agrees to this, still we are often stuck with half a decade old servers divided in far to low resourced build-agents.  
> The amount of benefit I've seen companies gain by moving to a faster test suite is one of the most important productivity benefits you can earn, simply because it impacts iteration feedback cycles, time to deploy, developer happiness, and inertia. Throw money at the problem: servers are cheap, developers are not.
    
A personal favourite; Use feature flags to enable new code paths in a controlled way at the right time. Also being able to shutdown the feature if it doesn't deliver or creates problems. 
> The huge benefit of all of this means that when you're ready to deploy your new feature, all you have to do is flip one line to true and everyone sees the new code paths

Later on in the article he describes that cleanup (specially of feature flagged branched code paths) should done afterwards to avoid building up technical debit. Important side note.
    
> The most important part of all of this is that you are responsible for your code. If it breaks, you fix it… not your poor ops team. So don't break it.
  
I don't agree to the next part: 
> When you're ready to deploy your new code, you should always deploy your branch before merging. Always.  
  
The idea is to release the branch, then the master branch is the previous known released version. When having a good branching and deploy strategy (and automated deploy tool), moving back to earlier released version is a push on a button, regardless of which branch or commit was deployed.  

## Control and monitor

Completely agree on the control/audit and traceable part. It should be clear for the whole team/company when, by who and what has been deployed. It should be clear from a monitoring/metric perspective also. Using a tool like NewRelic APM you can compare releases when deployments are marked using their API. This can be done from the deploy script.
  
If new issues or performance problems are popping up in production these can be quickly related if needed to a new release or changed feature. The post goes as far as detecting an higher error rate after deployment and doing an automated rollback based on that. Interesting idea.

# Go read the article
  
Nice written article, it hits some important points when you are involved in deploying software into a production environment. 



 