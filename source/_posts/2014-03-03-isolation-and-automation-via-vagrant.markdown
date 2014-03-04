---
layout: post
title: Isolation and Automation via Vagrant
subtitle: 
permalink: /issue09/isolation-via-vagrant
byline: Derek Hammer
category: issue09
authors: 
    - name: Derek Hammer
      twitter: 
      avatar: 
---

Anyone who has gone from developing on Unix to Windows can tell you the pain of crossing technical stacks. In spite of this, disparate tech stacks are common in many organisations. Even on the same team, developers, testers and operations can have different machine setups and tool choices. Sometimes it’s just down to personal choice. But it’s not necessarily a bad thing. Having consistency can cause innovation to stagnate and sometimes one tool really is better suited to a purpose than another. But what if you need your teams to cross-pollinate or merge together? 

>> “To have every engineer learn about the intricacies of each environment … would be completely impractical.”

To have every engineer learn about the intricacies of each environment that she may or may not be working in would be completely impractical and create an extremely slow ramp-up time. So what can you do to not spend inordinate amounts of time getting everyone in a state where they can actually do some work?  

Let me introduce you to Vagrant….

My current project faces the problem of normalizing our environments across a large organization. Historically the development group was split and that lead to a large divergence in practices, development techniques, tools and approaches to solving problems. Our goal is to overcome that divergence by having a team that combines elements of both groups. That team though, has its own challenges. Each team member has brought their own special sets of tools, machine and method of working, to the table. This has resulted in several technical stacks, each with its own knowledge silo that only a handful of people, or even just one person, on the team can operate.

Faced with this, the team has started to adopt Vagrant as a way to normalize, isolate and automate our environments. We looked at other tools like Boxen and Chef as ways to manage our machines, but quickly decided against them because of the ‘Bring Your Own Device’ nature of the team. Not to mention that Boxen would work only on Mac devices and we were dealing with Windows and Unix like environments. Chef works cross-platform, but gave less flexibility to the developer in how she set up her environment - we do use Chef as a way to manage the VMs, though.

Environment Consolidation
Some environments are more modern than others. Either because they are newer or have had recent investment. Some have technical debt that needs to be overcome in order to introduce a more modern toolchain. We have found that Vagrant solves many of the conflicts and difficulties that arose in our competing development environments. 

One conflict we face is the differences between workstations and upstream environments. We want to normalize the tools we use, so we did the following in each environment:

Development: We abstracted away the differences between Mac, Linux and - for the most part - Windows. Doing this was a great way to ensure consistency for engineers.
Production: To go just a step further, our Vagrant boxes are set up to use the same virtual machine image we use in the datacenter, where we deploy. In the words of Forrest Gump, "That's good! One less thing." 

Some of our tooling differs because of where and how we deploy. Some of our software, for example, runs and compiles under Java 7 while others are still on Java 6. Vagrant made this completely painless because of the isolation of virtual machines.

We were also easily able to introduce new tools into our environments. We are a large team and communicating the addition of a new tool or library or dependency - especially system packages - can be pretty cumbersome. Luckily, we just plop it into the provisioning part of our Vagrantfile - using chef-solo - and everyone is good to go after a simple `vagrant provision`.

>> ”Been on holiday for a week? ... you can be confident that when you return, a simple re-provisioning of the Vagrant box will get any tool changes you missed?”
Sunshine and lollipops
The introduction of Vagrant into our environment allows for any team member to jump confidently from one part of our code to another. They can have a fully functioning environment in at most, 15 minutes. A developer on a Windows machine can quickly jump into a new part of the codebase with her pair by bringing up the required Vagrant box and starting to poke around in the code. Been on holiday for a week? In our team, you can be confident than when you return a simple re-provisioning of the Vagrant box will get any tool changes you missed. And, if you’re using Chef or Puppet, easily see the differences in the log. Allowing a conversation like, "Why was gcc upgraded last week?" instead of the open ended, "What happened last week that I need to know about?"

Bonus features
In addition, Vagrant provides some nice bonuses to our development environment and workflow, including bringing new team members on-board quickly, finding bugs faster and to recovering from environmental quagmires...
New team member on-boarding
This is one of my favorites. How long does it usually take for a new team member to be ready to work on your team? We regularly on-board a new team members - either new to the team or that part of the codebase. It is really fun and empowering to say, "Here are the steps: 1. Check out the code, 2. Run ./go [1], 3. Take a 10 minute coffee break and you will be ready to go when you get back".
Recreating deployment schemes
We are also integrating many systems together that get deployed separately to different VMs in our Continuous Integration build and in production. It is relatively easy for us to set up a 'production-like' deployment on our local boxes. Bring up 2+ boxes, point them at each other - using the :private_network option in Vagrant - and run your tests to see the bug visible in a production-like scenario.
Easy nuclear option
When things go wrong and you've yak shaved for a hours, it can be really disheartening to have to resort to the 'nuclear option' and reinstall your operating system. With Vagrant, the nuclear option becomes easy. It's time for another coffee break and you'll be back up and running in no time.

⁂

Vagrant allows our team to easily maintain a productive working environment by normalizing many different workstation setups and isolating the particulars of our environments. Without it, our progress would grind to a halt.

If you think it is too difficult to get started, I challenge you to try create a Vagrant box for your next ‘from-scratch’ project. You can start with the "shell" provisioning and upgrade to Chef or Puppet from there. There are plenty of simple bootstraps to get you started, so stop wasting your time setting up environments and have coffee break instead.

[1] The "./go" script is a simple wrapper script that essentially does the following in any project we have: "vagrant up; vagrant ssh '/my/build/tool build'".

