---
layout: post
title: Isolation and Automation via Vagrant
subtitle: 
permalink: /issue09/isolation-via-vagrant
byline: Derek Hammer
category: issue09
authors: Derek Hammer
    - name: by 
      avatar: 
---
Anyone who has gone from developing on Unix to Windows can tell you the pain of crossing tech stacks. 

Having disparate tech stacks within an organisation is common. Even on the same team a developer, tester or operations team member can have  disparate machine setups and tool choices. Sometimes it’s down to just personal choice. But what if you need your teams to cross-pollinate? What if you need your team to cross these stacks or merge together? 

With a large number of different environments, it would either be completely impractical or have an extremely slow ramp up time for every engineer to learn about the intricacies of each environment that she may or may not be working in. So how do we make the ramp up easier and not spend inordinate amounts of time getting our machines in a state where we can actually do some work?  

Disparate stacks within an organisation are not necessarily a bad thing. Having consistency can cause innovation to stagnate and sometimes one tool really is better suited to a purpose that another. This leads large organisations to have teams with entirely different machine setups. 

Let me introduce you to Vagrant….

My current project is one that is faced with the problem of normalizing our environments across a large organization. The organization has a historical split in the development group that lead to a large divergence in practices, development techniques, tools and approaches to solving problems. Our goal is to overcome that divergence by having a team that combines elements of both development groups. That team, though, has its own challenges. Each team member has brought their own special sets of tools, machine and method of working to the table. This resulted in several technical stacks, each with its own knowledge silo that only a handful of people, or even just one person, on the team could operate.

Faced with this, the team has started to adopt vagrant as a way to normalize, isolate and automate our environments. We looked at other tools like boxen and chef as ways to manage our machines but quickly decided against them because of the Bring Your Own Device nature of the team. Chef would work cross platform but gave less flexibility to the developer in how she set up her environment [5]. Boxen would work only on Mac devices.

Some environments are more modern than others because they are either newer or have had recent investment into them. Some of our environments have technical debt that we need to overcome in order to introduce a more modern toolchain. We found that vagrant, though, solves many of the conflicts and difficulties that would arise in competing development environments. 

One problem conflict is the differences in workstations and upstream environments. We want to normalize the tools that we use on each of our environments.

* Development machine: We abstract away the differences between Mac, Linux and (for the most part) Windows. We all have different machines (different parts of the organization) and so having this done is a great way to ensure consistency for engineers.

* Production environment: To go just a step further, our Vagrant boxes are set up to use the same virtual machine image that we use in the datacenter where we deploy. "That's good! One less thing." as Forest Gump would say.

* Tooling differences: Some of our tooling differs because of where and how we deploy. Some of our software, for example, runs and compiles under Java 7 while others are still on Java 6. This is completely painless because of the isolation of virtual machines.
* New tooling introduction: We are a large team and communicating the addition of a new tool or library or dependency (especially system packages) can be pretty cumbersome. Luckily, we just plop it into the provisioning part of our Vagrantfile (we use chef-solo) and everyone is good to go after a simple `vagrant provision`.

What this meant?
This allows for team members to be able to jump confidently from one part of our code to another knowing that they can have a full functioning environment in, at most, 15 minutes. A developer on a Windows machine can quickly jump into a new part of the codebase with her pair by bringing up the Vagrant box and starting to poke around the code. A team member that has been on holiday for a week can be confident than we she returns that a simple re-provisioning of the vagrant box will get any tools that she missed[1]. 

Bonus features?
In addition, vagrant provides some nice bonuses to our development environment and workflow. It allows us to bring new team members of board quickly, find bugs quicker and to recover from environmental quagmires.

* New team member on-boarding: This is one of my favorites. We regularly on board a new team member (either new to that part of the codebase or just entirely new to the team). It is really fun and empowering to say "Here are the steps: 1. Check out the code, 2. Run ./go, 3. Take a 10 minute coffee break."[2]
* Recreating deployment schemes: We are also integrating many systems together that get deployed separately to different VMs in our continuous integration build and in production. It is relatively easy for us to set up a 'production-like' deployment on our local boxes. Bring up 2+ boxes, point them at each other (using the :private_network option in vagrant), and run your tests to see the bug visible is a production-like scenario.
* Easy nuclear option: When things go wrong and you've yak shaved for a few hours, it can be really disheartening to have to resort to the 'nuclear option' and reinstall your operating system. With vagrant, the nuclear option becomes easy. It's just time for another coffee break and you'll be back up and running in no time.

If you think that this is difficult to get started, I challenge you to try to create a Vagrant box for your next from-scratch project [3][4]. You'll find it easier than you think and much more maintainable in the long run.

Summary?
Vagrant has allowed our team to more easily maintain a productive working environment by normalizing many different workstation setups and by isolating the particulars of environments from each other. Without this setup, forward progress would slow and may even grind to a halt.

[1] And, if you are using chef or puppet, see the differences in the log quite easily. This will allow you to start a conversation about "Why was gcc upgraded last week?" instead of the open ended "What happened last week that I need to know about?"
[2] The "./go" script is a simple wrapper script that essentially does the following in any project we have: "vagrant up; vagrant ssh '/my/build/tool build'"
[3] If you are unsure, start with the "shell" provisioning and upgrade to chef/puppet from there.
[4] [Simple getting started with a bootstrap script](http://www.thisprogrammingthing.com/2013/getting-started-with-vagrant/)
[5] We still used chef as a way to manage the VMs, though.

