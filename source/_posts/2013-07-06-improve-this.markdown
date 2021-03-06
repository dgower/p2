---
layout: post
title: Improve This
permalink: /issue02/improve-this/
byline: The P2 Elves
category: issue02
authors:
    - name: by The P2 Elves
      avatar: pdp11-avatar.jpg
---
*In improve this we take a look at a reader submitted test, user interface, story or block of code and we try and improve it, without context, explaining what we did as we went.*

In this issue, Mike sent a link to an <a href='https://github.com/gardym/spacecubed-projectrjs/blob/master/lib/streamers/twitter_stream_source.js' target='_blank'>event source to a realtime social media visualization.</a>

Before we ever apply brainpower, let's apply computer power. JSLint and JSHint are both tools to find mistakes and oversights.

<div class='normal-gist'><script src='https://gist.github.com/gardym/721358c7f65836737415.js'></script></div>

The implied globals are all OK. The unused variables are not. We see immediately that:

1. The <span class='inline-code'>mongo</span> dependency isn't used<br />2. There is no error handling around inserting records into the database.

The first problem is easily solved. The second problem we'll report and ignore, because it appears throughout the rest of the program:

<div class='normal-gist'><script src='https://gist.github.com/gardym/7866987a3e0dfe1cae22.js'></script></div>

Let's apply brainpower. Three things stand out:

1. <span class='inline-code'>map_tweet_to_event</span> seems to have an unnecessary callback.  This *should* be an easy fix.

2. <span class='inline-code'>tweet.coordinates</span> is both null-checked and uses magic numbers.  This isn't a problem; but, data structures with optional nulls are easy to trip on in normal use and complicate testing.

3. <span class='inline-code'>start_streaming</span> is a set of deeply nested callbacks.  This one is four levels deep. Not a serious offence by Javascript standards; but, we can do better.

Sadly, this code came with no tests. We write a characterization test to give confidence that we won't break anything. The bottom of nested callbacks are good places to find expected behaviors:

<div class='normal-gist'><script src='https://gist.github.com/gardym/65dfdfd385020f6b8a0d.js'></script></div>

We flesh out the test guided by the test failures.

Now, we can refactor with (more) confidence:

First, we collapse the <span class='inline-code'>map_tweet_to_event</span> callback.

<div class='normal-gist'><script src='https://gist.github.com/gardym/14adb21c2f800ec16908.js'></script></div>

Second, we split up <span class='inline-code'>start_streaming</span> up by responsibility. Those responsibilities— right now— are:

1. Streaming tweets.<br />2. Logging.<br />3. Filtering tweets.<br />4. Saving raw tweets.<br />5. Saving events (processed tweets).

1 through 3 involve the Twitter stream. 4 and 5 involve the database.

We create a <span class='inline-code'>stream_tweets</span> function:" ,

<div class='normal-gist'><script src='https://gist.github.com/gardym/ff2d4371a7b429e00de1.js'></script></div>

Notice we inline the <span class='inline-code'>params</span> object that was previously initialized in <span class='inline-code'>track_current_user</span> because it is only used by the <span class='inline-code'>Twitter.stream</span> method.

Then, we create a <span class='inline-code'>record_tweet</span> function:

<div class='normal-gist'><script src='https://gist.github.com/gardym/e4c1d8372458c10795c9.js'></script></div>

This function returns the callback function, but keeps the <span class='inline-code'>db</span> in scope.
Finally, we update <span class='inline-code'>track_current_user</span>:

<div class='normal-gist'><script src='https://gist.github.com/gardym/b9a1a696c09805bbcd01.js'></script></div>

The tests pass! That means it works, right? ;-)

*Do you have something you want improved? Send it to <a href='mailto:p2@thoughtworks.com'>p2@thoughtworks.com</a>.*

<div class='byline'>All Gists brought to you by <a href='http://github.com/'>GitHub</a></div>
