---
layout: post
title: TheBot : Journey So Far
subtitle: 
permalink: /issue09/thebot-so-far
byline: Shantanu Tushar
category: issue09
authors: 
    - name: Shantanu Tushar
      twitter: 
      avatar: 
---

While working with Arduino and various sensors, a regular chore is to having to physically upload a new program to the arduino board. This is quite cumbersome at times and you will end up wasting lot of time and effort moving to the physical installation place for your arduino, connecting a USB cable and finally uploading a program.

The Solution
As we are all lazy programmers, that is something not to tolerate. What was described just now is way too much work if all you want to do is read a new sensor value of use a GPIO pin for output.

To make it easier, I wrote an arduino program (also known as a sketch) which does not hardcode the input and output pins. Instead, it waits and accepts this configuration over a wireless channel using cheap nRF24l01 modules. This way you can configure new sensors and/or make new pins to output signals without having to re-write the program. All this without disturbing your arduino sitting in a complex configuration in another room!

The code
All you need to do is to grab the repo at https://github.com/shaan7/arduino-sensor and follow the instructions. You will obviously need one nRF24l01 module each for Arduino and the Raspberry Pi which is actually going to configure and control the Arduino board.