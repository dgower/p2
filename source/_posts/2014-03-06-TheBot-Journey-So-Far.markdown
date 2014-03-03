---
layout: post
title: TheBot : Journey So Far
subtitle: 
permalink: /issue09/thebot-so-far
byline: Karan Misra
category: issue09
authors: 
    - name: Karan Misra
      twitter: 
      avatar: 
---

“ Robots that are controlled by node.js.” The idea imprinted on me immediately. 

“A crowd controlled robotic car!" 

A fun product with a tonne of learning potential. However, doing a "follow the blog posts/tutorials" stitch and patch job recommended on the NodeBots site did not excite me one bit. Sure, we’d done in two days, but what would we have learned in the process? 

Although I have worked extensively on node.js, the language did not interest me much - ambiguous syntax, callbacks, promises, etc. I had been looking for an opportunity do something real in Golang, and building a concurrent open source firmware for such a platform was just the ticket.
TheBot is first and foremost an experiment. An experiment aimed at research and learning. An experiment to kickstart a hardware engineering ethos in ThoughtWorks. Birthed as a crowd controlled robotic car that transmits video feed back to the controller; the vision has transformed many times during the development. Can it be the ultimate open source sensing/proximity prototyping platform? Should it be miniaturized and easy to mass produce? Could we extract a product out of this?

>> “TheBot’s value is the immense learning and research potential.”

On first appearance, TheBot looks like the result of odd inter-breeding between a remote-controlled car and the contents of your local Radio Shack. TheBot itself though, is not really just a car, it is actually a fully-fledged Golang based framework for working with hardware sensors and motor control. In it’s current incarnation, the RaspberryPi-based robot allows you to control it remotely using any device capable of running a modern browser. The on-board smarts do things like use rangefinders to implement collision avoidance, and you can even send it logo-ish commands like ‘turn 90 degrees right’.

Right now, we are laying down the rails for what is to come next. The modules are already taking shape and we are using our learnings from TheBot to drive the development of the framework(s) and the underlying hardware abstraction layer. 

Unique Selling Proposal: TheBot’s value is the immense learning and research potential in its current form. The fact that it looks like a car and has 4 wheels is just a bonus.
The Guts

We plan on doing a proper video walk through of the hardware soon, but until then:

Why Golang ?

Golang has excellent and remarkable support for concurrency in the core language. The RaspberryPi is not capable of running two threads of code in parallel. So we needed the car firmware to handle multiple real world interactions at the same time. Modelling this using threads would have forced us to use mutexes, etc, for synchronization. The ‘goroutines+channels' architecture in Golang helped us focus on the "actual" interactions (Goroutines are light weight threads which are executed via the Go runtime on real threads via a M:N mapping. Channels are a typed conduit for passing messages between goroutines). The resulting code is much easier to read, reason with and understand.

>> “Simply running the binary was always enough. This helped tremendously in shortening our development/build/deploy cycles and made the process even more gratifying.”

Golang is a statically typed, garbage collected and compiled programming language. However, in use, it feels like a FAST (slightly) verbose scripting language which has support for systems programming  and duck typing. It also has excellent support for cross compilation. Since the produced binary was entirely self contained and statically linked, no runtime was necessary on the RaspberryPi. Simply running the binary was enough, which helped tremendously in shortening our development, build and deploy cycles and made the process even more fun.
Why RaspberryPi ?

The RaspberryPi represents the lowest common denominator when it comes to platforms that are available to everyone. It contains a decent SoC (single core 700 Mhz ARM11) and runs Linux. Besides being an ideal target for a cross compiled Golang binary, it also doesn’t skimp (too much) on the I/O department I2C ✓ GPIO ✓ PWM support ✓. The swappability of the SD cards, the forgiveness of the hardware, USB power, integrated HDMI/Ethernet/USB ports; all these capabilities go a long way in making it a good first choice.

That being said, we could deploy the firmware, in its current form, on any Linux based platform that has the ability to talk GPIO/I2C, including:
BBB
Cubietruck
ODROID
Cotton Candy
CuBox
PandaBoard
Transcend WIFI SD Card (video)

In the long term then prognosis is a lot better. While Golang already supports a wide gamut of targets, I intend on running it on a raw microcontroller soon.
What does it do ? The Video

For its first public appearance at the Golang Meetup,  we wanted something to quickly showcase what the bot was capable of. I personally think it does a fairly good job:

[embedded video www.youtube.com/watch?v=iMXjkZ4B3EM goes here]
What next?

We did not necessarily limit ourselves to the current form factor when coming up with these ideas. Although the complete list available below, the best ones are:
End goals
Hobbyist / Education
Extract the components and make them available separately. Explore building a Super 8 kit (combine 8 of the most used sensors in one neat package.)
Logistics / Delivery
We see tremendous potential for this in the B2B space as well as in rural health care.
Home Automation
The existing solutions are tacky, expensive and lack a cohesive experience. We plan on using ThoughtWorks’ core competency, which is building well crafted custom software solutions, to revolutionize this space by coming up with something even your great grandpa could use.
New Capabilities
Gobotics
Golang robotics + hardware abstraction layer.
Better Acuity
Head mounted 3D display (think Oculus Rift) control of TheBot camera(s).
Route Mapping / Discovery
Not only should these robots (aerial or otherwise) be capable of efficiently navigating in chaotic environments, they need to account for the ever changing urban landscape. The firmware also needs the ability to react to the environment (think wind, rainfall, etc.)

⁂

The development process was nothing short of enthralling. We did not have well established libraries to lean back on. We went into this "batteries not included." The decisions were deliberate; to use Golang and not pre-existing libraries because the potential for learning would have been limited. We optimized for maximized learning. And boy did it pay off. Not only did we end up writing our very own Golang libraries for interfacing with all these sensors, we also had the opportunity to try and model the interactions of software with the real world. Imagine for one second: how many different ways there are there to make the car do a right turn. Things we take for granted in software actually open up a can of worms when the "real world" gets involved!

OK so the technical attractiveness of such an undertaking is obvious, but this there is more to it than that. I believe that a lot of good can be done for the "voiceless" by getting cheap commodity devices into their hands. A simple 2G connected solar powered open hardware device that allows a village like Panchayat, India, to bypass all the middle men and leverage social networking to report grievances to their congress representative. This could bring about a revolution. Which minister worth his salt would want to look bad on Facebook, right? Our hope is that the resulting learnings/framework from TheBot effort can and will make this possible. 

The possibilities are truly endless.

Credits

Contributors in no particular order: Sapto, Rohit, Kunal, Nikesh, Shantanu, Hanu, Gagan, Shaunak, Kashyap, Mukund, Akhil, Vishwas, Mallik, Deepthi, Shaun, Nag, Bala & Sam Newman.


