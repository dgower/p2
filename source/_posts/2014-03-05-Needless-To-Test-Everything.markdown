---
layout: post
title: Needless To Test Everything
subtitle: 
permalink: /issue09/needless-to-test
byline: Raman Kansal
category: issue09
authors: 
    - name: Raman Kansal
      twitter: 
      avatar: 
---

Supposed to test everything, bug can be anywhere, do not trust developer blindly, do not mix multiple tests in single test and many more such things revolves around QA mind while writing automation tests. Without compromising the functionality we should also need to think of strategy to automate particular test. Sometimes there are multiple ways to automate a test & we should analyze different aspects like scope, effectiveness, cost (time/effort) & maintenance before jumping to automate the test.

We like to share one of scenario we faced in OpenLMIS project, one of the module in this project require offline functionality. As per this requirement user can fill data in multiple forms on web application without internet connectivity. We implemented IndexedDB as browser data storage solution. 

When this functionality come for testing, it was quite easy to test manually as we can verify data stored locally in IndexedDB but how to validate same through automation scripts. Straight forward solution was to enter data & write code to verify same in IndexedDB without going offline but we need to analyze that whether it is a best solution in terms of ease, scope & maintainability. For validating indexedDB we need to write similar javascript code which developers has written to insert, update, delete & fetch records from indexedDB. Is it really worth putting that effort?

What we did, We verified data on forms itself after entering, modifying & deleting in offline mode (without internet) & after clearing local cache. This way it guarantee us that data is stored locally, it is not lost & nothing available on server DB. But we have not verified that data has stored in indexedDB & schema is correct or not. In this way we made sure that end-end solution is working rather than particular piece of functionality.


Notes from call:

QA - OpenMILS project

automate as much as possible
- do not resets manually what you have done

specialy about this app
- have to store data locally - on users machines
- allow internet less access - offline mode

Handling offline mode
- update on the server later

used indexed to store data locally on a browser cache
- each browser ff, i.e., chrome not safari
- any that comes with browser
- stories rapidly - multiple forms in offline mode
- something you have to handily in places like africa
- while trying to automate the func
- devs wrote api in js
- automate through selenium
- have to write the same js code
- totally redundant and duplicated
- do not test everything through automation
- rather than verify in index db

- in offline mode pushed the data and verified 
- enter data 
- clear cache 
- check the data is still present - don't verify index db directly
- verify it indirectly
- then in online check it appears from PostGres
- indirectly without testing indexed have verified functionality
- QA should look other testing

- in the selenium we are doing it in offline
- not verifying index db 



