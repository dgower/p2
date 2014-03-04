---
layout: post
title: Why should I hire a polyglot programmer?
subtitle: 
permalink: /issue09/why-hire-a-polygot
byline: Rouan Wilsenach
category: issue09
authors: 
    - name: Rouan Wilsenach
      twitter: 
      avatar: 
---

It’s common for people to be sceptical of software developers with varied coding experience. We're used to seeing, “5 years C# experience” on the CV in front of us, so when we see a CV that says: “2 years of Ruby, 1 year of Python and 2 years of Java”, we might be concerned that the person doesn't have the depth of experience we need.  Although this reaction is natural, it’s misguided.
>>”If it doesn't matter whether the programmer you're considering has deep knowledge of the language your application uses, what does?“
The person with the second CV could be a better developer on a C# project than your language expert, despite having little or no C# experience. Let’s not confuse them with a developer who happens to know a few languages. I’m talking about a particular kind of developer with varied experience and a good grasp of engineering fundamentals. The polyglot programmer.

pol·y·glot
ˈpäliˌglät/
adjective
knowing or using several languages.

If it doesn't matter whether the programmer you're considering has deep knowledge of the language your application uses, what does? How are you meant to decide whether a coder is up to the task? How do you know they'll be able to pick up C# and add value to your project without slowing you down?
Let me set the scene...
Your organisation's technology stack is .NET. Your team is a group of seasoned .NET developers and their experience ranges from 5-15 years. Let's say you hire the person with the second CV.
Ana, has a number of years of experience under her belt, but none in .NET. In spite of the scepticism of the team, Ana quickly picks up C#. She is not only able to keep up with the team, but ends up teaching them many new things. 
Why?
It’s all about the basics
Software engineering is about more than the language you're using. In my experience, the developer you want on your team is often the one that understands these fundamental software engineering practices:
Automated testing
Automated tests give us confidence that our software does what it's meant to. The developer you hire should understand this and ensure that testing is a first class concern in your development process. Developers who are passionate about testing tend to be intolerant of those who are not. With your support, expect your new hire to quickly get the rest of the team writing tests.
Design
When I talk about design, I'm not thinking of UML diagrams or planning out the details of the application in advance, which could potentially make it difficult to change. I’m talking about having an awareness of what good code looks like and ensuring that the team is constantly making the small changes required to ensure the code stays that way. The programmer you want to hire understands emergent design and object oriented programming. They know how to refactor code to make it easier to work with, regardless of the language they are using.
Deployment
Your software is worthless unless it is in production. No matter how innovative the features are, if a user cannot use it, it’s pointless. When you hire a developer who knows how to automate the deployment and configuration of your applications, you gain the potential to move quickly on new ideas and confidence that your application can recover from disasters. 
These skills cross-cut languages and a developer who really understands how to apply these practices in one language can port their knowledge to another.
Varied experience
Ana notices that the assertions the team are writing in their tests are clumsy. The tests don't read well and the error messages don't provide much detail when they fail. In her Java days, she used a library called Hamcrest that made assertions read more like English and provide clearer error messages on failure. She asks herself “Is there something like that for .NET?” With a quick search, she finds FluentAssertions. To her delight, it has cleaner syntax than the Java library she’s used before, thanks to C#'s extension methods.
Ana realises the team deploys their application manually. She has automated a number of deployments in Unix and, even though there are more sophisticated tools available, believes a bash script is an improvement over manually deploying. She does some digging and comes across PowerShell. She starts writing some PowerShell scripts to automate the deployment. The syntax is a bit clumsier than Bash, but a lot of it is the same. Soon she has a script up and running that copies the application DLLs and gets the web server to serve the updated files. She asks herself whether there's a way to test all this PowerShell she’s writing. Ana finds a testing framework called Pester and tests the scripts she’s written.
The team is taken aback. They've never even tried automating their deployment, and some Windows newbie has just written scripts to do it in a Microsoft language. And it’s tested! Who knew you could test scripts?
A polyglot programmer can open your team's eyes to the development practices and tools that are common in other languages.
The right tool for the job
Not all applications are the same. The problems they seek to solve vary greatly. Knowing multiple languages allows you to pick the right technology for the problem at hand. Why should you care? Software built on the wrong technology stack can be unnecessarily complex and painful. For example, using Java to solve a clearly functional problem, when Clojure would be simpler. Or building a Rails app when your users want the kind of fluid interface a single page JavaScript framework can give them.
Hiring a Polyglot Programmer allows you to use their breadth of experience to help you make smart decisions on your technology choices.
I'm sold! Where do I find one?
This is the hard part. Poor development practices are widespread in the industry. If you find a developer who matches the criteria I've described, snap them up! Remember to look for more than their experience in your language or framework on their CV. What do they know about quality software design and testing? What is their experience in putting their code live?
>>”If you can't find a good polyglot programmer, then you have the power to create one!“
I'm not saying that deep knowledge of a language or framework isn’t useful. It's often important, so don't run off and fire your team of language experts. The point I'm making is that a polyglot programmer brings a set of valuable general skills and can learn the specifics as they go.
⁂
The good news is that, if you can't find a good polyglot programmer, you have the power to create one! Encourage your development team to broaden their skill set, give them the time to experiment with new languages, frameworks and tools. And, most importantly, make sure you're helping them build those crucial fundamental skills. Those skills that differentiate a great developer from a decent one, no matter which language they're coding in.
