---
layout: post
title: "TDD is a feedback tool, not a religion"
date: 2014-05-17 15:48
comments: true
categories: 
---

ICYMI, there’s currently a discussion going on around TDD, after [DHH](https://twitter.com/dhh) declared it ‘dead' at RailsConf 2014. This lead to a discussion series between himself, TDD legend [Kent Beck](https://twitter.com/KentBeck), and [Martin Fowler](https://twitter.com/martinfowler), the second of which took place on Google Hangouts yesterday:

<iframe width="560" height="315" src="//www.youtube.com/embed/JoTB2mcjU7w" frameborder="0" allowfullscreen></iframe>

In this discussion, David makes the claim that TDD leads you down a path of aggressive and unnecessary isolation of your code, citing ‘Hexagonal Rails’ as an example of the damage that TDD does when applied absolutely:

[https://gist.github.com/dhh/4849a20d2ba89b34b201](https://gist.github.com/dhh/4849a20d2ba89b34b201)

I think most people would find the code in the example pretty poor. The intent of the code is heavily obscured, and I find it hard to read. This kind of isolation might make sense when working on a larger, more complicated domain, but given the complexity of this example, it's absolutely overkill.

The question is "Was TDD responsible for the author arriving at this design?". DHH paints hardcore-TDD practitioners as dopamine addicts; constantly craving their next fix of the 'Red-Green-Refactor' cycle, they will do anything to make their speed though this cycle quicker. It’s certainly true that code this heavily isolated is easy to unit test.

It shouldn't be a surprise that TDD acts as a force on your code, that feedback is the reason we choose to write tests first. [Gary Bernhardt](https://twitter.com/garybernhardt)'s post [Test isolation is about avoiding mocks](https://www.destroyallsoftware.com/blog/2014/test-isolation-is-about-avoiding-mocks) touches on this idea:

"Most of us think that small functions are better, yet hundred-plus line functions are common [...] The reason is that there's no pressure exerted on us."

TDD applies this pressure, by forcing you to interact with the APIs your code exposes, and create the dependencies it requires. This feedback acts as a tool which helps you feel the pain in your design.

However, this doesn't mean that to practice TDD is to surrender all control to our tests and powerlessly slip into an obsession with faster and smaller units. It remains up to the developer to interpret test feedback, amongst all the other feedback and intuition that they have, and make sensible decisions.

The vast majority of people using TDD do not blindly let it destroy their designs, creating an ever expanding number of classes, repositories and service objects. Instead, they see it for what it is: Not a silver bullet or religion, but a tool which helps you make better design decisions.

Before I wrap this up, I’d like to thank DHH, Kent, and Martin for having these discussions. Despite some of the more troll-y posts, I think the general dialog around #isTDDDead has actually sparked some quality debate, and it has driven me to some new insights about how I write and test code. Hopefully we can all remember we're still figuring this out, and treat this as an opportunity to learn.
