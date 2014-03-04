---
layout: post
title: TheBot : Two months early and 300K under budget
subtitle: 
permalink: /issue09/two-months-early
byline: Dave Elliman
category: issue09
authors: 
    - name: Dave Elliman
      twitter: 
      avatar:  
---

It was a sunny Thursday afternoon. An intrigued, but slightly dubious Technical Architect, Dan, left our ThoughtWorks presentation.

Could Clojure be used to build the bespoke CMS? Is it too bleeding edge? Would his team get it?  

But lets take a step back. Why would a large organisation with a mix of technologies and legacy systems want to muddy the waters with a completely new language?

A while ago we engaged with Dan’s company. Their business model was shifting more towards a digital presence and they needed a platform to build for the future. They wanted to utilise as much of their older back end systems as they could. They knew rebuilding their entire platform from scratch, “the big rewrite”, is an anti-pattern.

>> “Why would a large organisation with a mix of technologies and legacy systems want to muddy the waters with a completely new language?”

Their teams’ current skill-sets leant them towards Java, but the important thing to us was the feeling that we could genuinely deliver quickly and meet their deadlines. 

A few months in we were about to start a smaller project within the larger program of work. We needed to add content management to a number of potential web site instances. We began by reviewing available CMS tools in the market. After some research it turned out that none of the off-the-shelf CMS tools available would meet their required approach in the way we needed, so we decided to build our own. 

We already had a continuous delivery pipeline set up from the main project that we could adapt, we just needed the right technological choices that would deliver business value in an innovative way to meet our deadline. We knew we had to use the JVM, but building what was to be an app used by partnering digital agencies and client staff, needed to be robust and work intuitively. After brainstorming some ideas we decided to put forward the idea of a Javascript based Single Page App (SPA) with a Clojure back end and a set of small Clojure based micro services sitting on top of MongoDB hosted in Rackspace. 

Dan wasn’t easily convinced. He took some persuading...

We had to present the pros and cons of polyglot programming using the JVM as the basis of the agreement, rather than just using Java. 

Dan still wasn’t convinced...

We discussed the existing Clojure community, the maturity of the language itself and the momentum we saw in the industry. Companies are seeing speed to market deliveries, that are based on Clojure. 

Dan decided to test out the theory. 

If he, someone without a development background could get Clojure, then surely his team of Java developers could too.

He had recently built an app to collect data about the various sites the company hosted in different places and had used Java and Spring MVC. He locked himself away for the weekend and rebuilt his app... in a fraction of the code. 

The following Monday we got an email from Dan.  

“I am more than happy to go ahead with the use of Clojure.” 

Win.

Given the go ahead, we started our usual project inception activities and started delivering the application. We decided to split the services so that one service would provide content to its consuming web sites that were responsible for all layout decisions given the content components and some meta data about it, and another service was responsible for maintaining it. The Javascript SPA used the second service directly as well as domain specific services on the main project platform - we were also building in parallel. 

The first deadline was 6 weeks away. No-one expected us to hit it. We had started a week late due to internal governance and we were using a new technology the team didn’t know.

We were careful to structure the iterations and get the right things done in the right order. We engaged with user testing in early pre-development to get the designs and user experience conversations going. The users were accustomed to traditional CMS’s, an approach we had eschewed because of the varying outlets for the content - we didn’t want to enter ‘template hell’. We worked with the client to establish acceptance criteria and trained their internal users on how create the necessary content. We released every day to a pre-production environment so the users could test early and often.

The process continued with the team delivering and the users creating content on the application, an application constantly growing in capability. 

We hit the deadline a week early.

It was no big deal. We were delivering everyday, multiple times a day. We had delivered everything for phase 1 of the product two months early and way under budget. But how much of this was due to the process? How much to do with it being an SPA, Clojure, or the team? 

>> “After a couple of iterations no-one talked about learning curves anymore.”

Success is always an aggregate of all these factors. Most of the team members had very little Clojure experience when they started. They wanted to know how they would do TDD, what IDE if any they would use, what was a REPL etc. After a couple of iterations no-one talked about learning curves anymore. They just got it.

Engaging a client when you are sure an innovative solution would better serve the problem is key. It’s a rite of passage for everyone. At ThoughtWorks we are fortunate that we have a large pool of experience to reach out to as well as strong community links, all of which helped in our cause. The key is not to be afraid to try it out. Create a low risk way to do this, like Dan did. Test out and prove your theory. 

Software creation is a design process and design goes through many iterations until you get it right. That includes the tools you choose. 
