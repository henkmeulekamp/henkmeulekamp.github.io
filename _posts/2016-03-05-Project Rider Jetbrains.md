---
layout: post
title: Project Rider GIT Ignore
---

Project Rider is a new C# IDE based on ReSharper and the IntelliJ platform.
  
The EAP is for download if you signup on the Jetbrains site. First try outs indicate its a nice C# IDE. 
Not sure if it is any better then VS2015 or VS Code. Doing some first tests now and it does work good on console apps. It opens SLN files, compiles console apps and runs them in debug mode. It did lockup completely on intelisense when trying to add Linq methods to a dynamic type object instance.
  
Just wanted to post the GIT ignore inclusions here as a reference:  
`#RiderC#`  
`.idea//`  
`*.*.iml`  
  
This should prevent .idea/ folder content and *.*.iml files to be added to your GIT repo. These two file/folder types are added to the repository folder as soon as you open up a SLN file in Project Rider IDE.
  
The visual studio reference GIT ignore file on Github has the same to additions as well:
[VisualStudio.gitignore](https://github.com/github/gitignore/blob/master/VisualStudio.gitignore)
  
 