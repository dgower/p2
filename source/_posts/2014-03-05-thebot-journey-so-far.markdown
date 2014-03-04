---
layout: post
title: “TheBot : Journey So Far”
subtitle: 
permalink: /issue09/thebot-so-far
byline: Karan Misra
category: issue09
authors: 
    - name: Karan Misra
      twitter: @kid0m4n
      github: github.com/kidoman
      avatar: karanmisra-avatar.jpg
---

“ Robots that are controlled by node.js.” The idea imprinted on me immediately. 

“A crowd controlled robotic car!" 

A fun product with a tonne of learning potential. However, doing a "follow the blog posts/tutorials" stitch and patch job recommended on the NodeBots site did not excite me one bit. Sure, we’d done it in two days, but what would we have learned in the process? 

Despite having worked extensively on node.js, the language did not interest me much - ambiguous syntax, callbacks, promises, etc. I had been looking for an opportunity do something real in Golang, and building a concurrent open source firmware for TheBot was just the ticket.
TheBot is first and foremost an experiment. An experiment aimed at research and learning. An experiment to kickstart a hardware engineering ethos in ThoughtWorks. Birthed as a crowd controlled robotic car that transmits video feed back to the controller; the vision has transformed many times during the development. Can it be the ultimate open source sensing/proximity prototyping platform? Should it be miniaturized and easy to mass produce? Could we extract a product out of this?

>> “TheBot’s value is the immense learning and research potential.”

On first appearance, TheBot looks like the result of odd inter-breeding between a remote-controlled car and the contents of your local Radio Shack. TheBot itself though, is not really just a car, it is actually a fully-fledged Golang based framework for working with hardware sensors and motor control. In it’s current incarnation, the RaspberryPi-based robot allows you to control it remotely using any device capable of running a modern browser. The on-board smarts do things like use rangefinders to implement collision avoidance, and you can even send it logo-ish commands like ‘turn 90 degrees right’.

Right now, we are laying down the rails for what is to come next. The modules are already taking shape and we are using our learnings from TheBot to drive the development of the framework(s) and the underlying hardware abstraction layer. 

Unique Selling Proposal: TheBot’s value is the immense learning and research potential in its current form. The fact that it looks like a car and has 4 wheels is just a bonus.
The Guts

We plan on doing a proper video walk through of the hardware soon, but until then:

Why Golang ?

Golang has excellent and remarkable support for concurrency in the core language. The RaspberryPi is single threaded and we needed the car to handle multiple real world interactions at the same time. Using threads would have forced us to use mutexes, etc, for synchronization. The ‘goroutines+channels' architecture in Golang helped us focus on the "actual" interactions (Goroutines are light weight threads which are executed via the Go runtime on real threads via a M:N mapping. Channels are a typed mechanism for passing messages between goroutines). The resulting code is much easier to read, reason with and understand.

>> “Simply running the binary was always enough. This helped tremendously in shortening our development/build/deploy cycles and made the process even more gratifying.”

Golang is a statically typed, garbage collected and compiled programming language. However, in use, it feels like a FAST (slightly) verbose scripting language which has support for systems programming  and duck typing. Since the cross compiled binary was entirely self contained, no runtime was needed. Simply running the binary was enough, which helped tremendously in shortening our development, build and deploy cycles and made the process even more gratifying.
Why RaspberryPi ?

The RaspberryPi represents the most available lowest common denominator; a ARM chip running Linux. Besides marrying well with cross compiled Golang, it also doesn’t skimp on the I/O department I2C ✓ GPIO ✓ PWM ✓ The forgiving nature of the hardware, integrated HDMI/Ethernet/USB go a long way in making it a good first choice.

That being said, we could deploy the firmware, in its current form, on any Linux based platform that has the ability to talk GPIO/I2C, including:
BeagleBone Black
PandaBoard, etc.

Our long term goal is to be able to target raw microcontrollers.
What does it do ? The Video

[embedded video www.youtube.com/watch?v=iMXjkZ4B3EM goes here]
What next?

The current form factor was an evolutionary step; a convenience which allowed us to get started quickly. 

We definitely want to cater to the hobbyist / education space (possibly in the form of a stripped down, dressed up Super 8 sensor kit, to help people get started quickly) as it has the potential for maximum impact at the grassroots level. At the same time, we want to balance things out by looking at solidly marketable areas like B2B logistics / delivery (it sort of applies to the rural health care space as well) and home automation. The home automation space is particularly exciting as the potential for integration between really smart software and hardware innovation is really high (as aptly demonstrated by the NEST devices.)

To make the above happen, we will need to stretch TheBot’s legs and expand its capabilities. We are in the process of extracting a hardware abstraction framework (called EMBD) which will allow us to target a variety of hosts (RPi, BBB, etc.) from a single code base. This would be particularly helpful because it would allow to quickly prototype solutions using readily available hobby boards, while still retaining the ability to target the final hardware. Besides that, we are also interested in route mapping / visualization, as capability in this area will open a whole bunch of opportunities. 

⁂

The development process was nothing short of enthralling. We did not have well established libraries to lean back on. We went into this "batteries not included." The decisions were deliberate; to use Golang and not pre-existing libraries because the potential for learning would have been limited. We optimized for maximized learning. And boy did it pay off. Not only did we end up writing our very own Golang libraries for interfacing with all these sensors, we also had the opportunity to try and model the interactions of software with the real world. Imagine for one second: how many different ways there are there to make the car do a right turn. Things we take for granted in software actually open up a can of worms when the "real world" gets involved!

OK so the technical attractiveness of such an undertaking is obvious, but this there is more to it than that. I believe that a lot of good can be done for the "voiceless" by getting cheap commodity devices into their hands. A simple 2G connected solar powered open hardware device that allows a village like Panchayat, India, to bypass all the middle men and leverage social networking to report grievances to their congress representative. This could bring about a revolution. Which minister worth his salt would want to look bad on Facebook, right? Our hope is that the resulting learnings/framework from TheBot effort can and will make this possible. 

The possibilities are truly endless.
Credits

Contributors in no particular order: Sapto, Rohit, Kunal, Nikesh, Shantanu, Hanu, Gagan, Shaunak, Kashyap, Mukund, Akhil, Vishwas, Mallik, Deepthi, Shaun, Nag, Bala & Sam Newman


