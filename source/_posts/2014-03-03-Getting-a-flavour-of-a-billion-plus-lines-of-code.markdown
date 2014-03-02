---
layout: post
title: Getting a flavour of a billion plus lines of code
subtitle: 
permalink: /issue0/getting-a-flavour
byline: Dan Abel
category: issue09
authors:
    - name: Dan Abel
      twitter: 
      avatar: 
---
Story
At a global media company, we needed to summarise the clients current state, and one of my jobs was to get a flavour of code quality. 

Once I started looking I realised how big that challenge was - even if I could get access to it all, there was more code that I could possibly look at. Upwards of 1200 repositories and more than a million million lines of code. Reader, I struggled with the enormity of it. Oh didn't I mention - we needed to be done in two weeks. 

Mission Impossible? 

Given the challenge of having an opinion of more code than it was possible to look at, let alone consider fully, we had to try some different approaches to the problem.

We struggled to find a compelling interpretation of the data until we tried comparing the results we were getting with the results from well known and used open source projects. With that we got compelling stories that the business could use to decide on the need for changes and explain why to their staff

What we did

Tried to get a good span across the repositories - a sample would give us a flavour: 10 million lines of code
Collect data through a number of passes and start to infer 
Start simple, stay at scale, use basic tools such as grep to discover lines of code, lines of test code etc, 
Decided on some core languages that allowed us to apply a single tool (source monitor) to get complexity metrics - Lines of code and lines of tests as a core measurement of risk
Zoom in to look for whys - XML files, tools use via libraries etc
What happened
Complexity: Some code broke the tools. Weren't able to use visualisations
had data but without context it we could compare projects but was it oranges and apples
needed a baseline: selected well known/respected open source projects and performed same analysis on them.
Gave is a solid platform to talk about the code and something its quickly possible to get an opinion on

Some more details
https://my.thoughtworks.com/groups/siq-initiative/blog/2011/05/03/code-tech-debt-analysis-at-thomson-reuters

