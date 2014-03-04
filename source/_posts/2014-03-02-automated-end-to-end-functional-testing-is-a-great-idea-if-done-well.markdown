---
layout: post
title: Automated end to end functional testing is a great idea... if done well
subtitle: 
permalink: /issue09/Automated-end-to-end
byline: Chirag Doshi
category: issue09
authors:
    - name: Chirag Doshi
      twitter: chiragsdoshi
      avatar: chiragsdoshi-avatar.jpg
---

I have been on and seen just too many projects where the promise of automated end to end functional tests backfires or at least doesn't pay back enough positive results, Here is my take on why.
Before (on several projects earlier)
We used to do the following:
Devs would TDD their code and thus write enough unit tests
Devs would also write a couple of integration tests to tests integrations like db access, talking to a file system, external service etc.
QAs would try and write a couple of automated end-to-end tests as part of testing each user story

This would mean that in about 6 months of development:
We would have many unit tests (500+)
We would have a few integration tests (around 10-20)
We would have many automated end-to-end tests (100+) .

The fact that we have so many end-to-end tests, testing scenarios for every single user story(almost) is the reason why I think our end-to-end tests start becoming too hard to maintain and run due to all the issues that you point out like tests take too long to run, they fail unpredictably and generate false alarms, too much time is spent in debugging and maintaining these tests.

Now (What I try to push for on projects these days - for web apps)
We would like to do the following
Devs TDD their code and thus write enough unit tests (exactly like earlier)
Devs also write a couple of integration tests to tests integrations like db access, talking to a file system, external service etc. (exactly like earlier)
Devs write view level tests to check presence of key data in the html output (as much as possible based on the MVC framework in use). they also write controller level tests
Devs write Javascript tests to test any(significant) ui logic
Devs or QAs write a few (end-to-end minus UI) tests for every story. This would have an impact (I think positive) on the architecture of the system. It would result in creation of an Services API of some sort (whether it is deployed as an independent app or not is a seperate question)
QAs write a very few end to end tests (using selenium like tools). The aim of these tests would be do a quick sanity check of the integration of the UI with the rest of the application. I believe these should be max 10-20 in number and should mimic the most commonly used user journeys in the system

I think doing the above solves many of the problems you have pointed out, it would provide the following benefits.

We would still have a good level of confidence in release frequently since the overall coverage of the different parts of the system is  as high as before.
QAs need to write and maintain very few end to end tests (~10 instead of ~100). It would be easier to keep these tests green, they will run fast and the QA will have the time to focus on other kinds of testing manual testing, exploratoy testing, cross browser look and feel testing, performance testing etc.


If you found this post interesting, you should read one of my earlier posts too, it is based on a similar idea: The Story of a QA

Notes from call
- key takeaway - automated - we sometimes go overboard or do it wrong
- invest in wrong tests and don’t get the value
- e.g. lots of time spent on browser/ui test - these test are then very brittle
- it is important to test the UI - but leave all variations of data and logic at the lower layers of your architecture
- How to solve it?
- main point - need tests to cover core user flows
- critical user journeys - at least one test through the entire cycle
- lots of variations - UI tests for these is an anti-pattern
- push those tests down

