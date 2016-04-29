---
layout: post
title: "The Very Basics of Vim Registers"
date: 2016-04-29 15:33:00 -0500
comments: true
categories: 
---

## But Why?

Registers open up a world of possibilities in Vim. If you're not using them, then you're potentially limiting your Vim productivity.

For example, how many times has the following situation happened to you?

You want to copy a line of text so you:

1. Yank the line in question

2. Delete another line along the way

3. Attempt to put the original line, accidentally putting the deleted line

{% img http://seanbw.com/images/vim_registers1.gif %}

This was a major hurdle while switching from RubyMine to Vim full time. Luckily I had a much more experienced, handsome coworker (shoutouts to Tony) who revealed to me the awesome that are Vim registers.

To see them in action yourself, open Vim and type `:reg`

No, seriously, do it. I'll wait.

{% img http://seanbw.com/images/waiting.gif %}

Want to put the last line you yanked and NOT the last one you deleted?
Use the `0`th register.
`"0p`

Cool right? Now, let's go over another example.

## Named Registers
Another fantastically useful feature of registers are named registers. This gives you the ability to store text under an alias for later use.

In this example I copy the final line to the 'a' register with:
`"ayy`
and you then you can see it in the 'a' register!
This text can later be put with:
`"ap'

{% img http://seanbw.com/images/vim_registers2.gif %}

## Final Thoughts
We've only scratched the surface on what's possible with Vim registers. [Use Vim](http://usevim.com/2012/04/13/registers/) and [Vim Casts](http://vimcasts.org/episodes/meet-the-yank-register/) both have excellent tutorials for more information.



