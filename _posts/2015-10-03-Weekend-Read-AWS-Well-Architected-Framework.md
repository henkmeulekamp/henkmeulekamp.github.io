---
layout: post
title: Weekend Read: AWS Well Architected Framework
---
  
AWS Solution architects published a guidance document this week on how to create well architected solutions in the AWS cloud.
  
You can find the [pdf here](http://d0.awsstatic.com/whitepapers/architecture/AWS_Well-Architected_Framework.pdf)
and [announcement here](https://aws.amazon.com/blogs/aws/are-you-well-architected/).
  
The AWS Well-Architected Framework is based around four pillars:  
- Security
- Reliability
- Performance Efficiency
- Cost Optimization
  
Its a 56 page document (32 readable, other 20 something appendixes) and easy to read. It is very usefull when planning on setting up a larger solution in the AWS cloud. Its mostly setting up some principals/ideas and questions to ask and then explaining which products and services in the AWS solution can help in those cases.  
  
Would I read it when not having anything in the AWS Cloud? Maybe not, but I do believe AWS (With Azure) is currently a frontrunner in the new way of hosting, where IaaS is completely automated and available for anyone with just creditcard. Some of the ideas and questions will be applicable for any developer/engineer responsible for running larger software solutions.
  
Interesting ideas:  
  
**Failure management:**  
> "Also, rather than trying to diagnose and fix a failed resource that  
> is part of your production environment, you can replace it with a new  
> one and carry out the analysis on the failed resource out of band"  
  
**Use server-less architectures:** 
> "In the cloud, server-less architectures remove the need for you to run  
> and maintain servers to carry out traditional compute activities."  
  
**Databases:**  
> "Treat the database as code to allow it to evolve over time rather than  
> be a one-time fixed decision. Use test data to identify which database   
> solution matches each workload best"  
  
  
  
 
 