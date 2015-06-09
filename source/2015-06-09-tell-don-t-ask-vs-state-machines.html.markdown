---
title: Tell Don't Ask vs. State Machines
date: 2015-06-09 01:59 UTC
tags:
---
 
# Tell Don't Ask vs. State Machines


About two nights after I came back from RailsConf 2015 in Atlanta, I got up at least 8 times and scribbled out around 10 pages of notes on removing conditionals from Rails codebases (read: my company's codebases). This sleeplessness and these notes were a side-effect of exposure to Sandi Metz's fantastic talk [Nothing is Something](https://www.youtube.com/watch?v=OMPfEXIlTVE). I'd like the missed sleep back.

You should probably watch the talk as the rationale for this post and the post itself will probably make more sense with that context.

And I am aware that Sandi Metz didn't invent "Tell Don't Ask" and there have been many talks on it in the past (Jim Gay, a good friend of mine, gave [this talk on East-Oriented Programming](https://www.youtube.com/watch?v=kXcrClJcfm8) at RubyConf 2014). However, for some reason(s) most likely having to do with certain thoughts about design and architecture being more prominent in my head at the time than at other times in the past, Metz's talk was the one that really flipped something in my head and led to sleeplessness (sorry, Jim).

## Tell Don't Ask (and some implications)

"Tell Don't Ask" is the idea that Metz mentions first: the avoidance of conditionals. After all, she states that they are Type Checks, the bane of Objects. So what does avoiding conditionals (and predicate/interrogator methods) mean? Well, loosely speaking, it means we can't really ask our code questions. But code still has to make decisions, right? Being of a reflection of a business process where decisions are required, doesn't our code need to make decisions too? Yes, yes it does. So, where do the decisions go?

Well, I really like the idea that we shouldn't have conditionals or decisions in our code. It makes everything wonderfully simple. But as previously mentioned, it doesn't work in non-trivial applications. So what if we try to keep conditionals and decision structures out of our business logic and domain objects? Yeah, that seems doable. This might actually work.

One of the really interesting implications of forcing decisions out of the business logic is that, to ensure the kind of smooth sailing that decisionless code would realize, the objects involved in said code would have to have to come configured from the factory with all the decisions already made. This is how real-world manufacturing actually works; your laptop doesn't ask you whether you want a wifi card everytime you boot it up, you specify that when you order it.

Hang on, that actually seems like a pretty good metaphor. What if we had some kind of object manufacturing process that preconfigured an object so that it would behave exactly as expected without being questioned about a thing as it sailed smoothly along the conveyor belt that is our business logic?

And now we come to our Rules:

## The Rules

1. Questions **may not** be posed to objects inside business logic.
2. Questions **may** be posed to objects at the boundaries of our application.

These are really just simple, punchy distillations of the above discussion. For every place where we would have had a decision in our code, we need to drag that decision (kicking and screaming) all the way to a system boundary (there's actually the possibility for some really interesting observations of boundaries involving where decisions stop being made; another time maybe).

So what is counts as a system boundary for the Rules? Two obvious ones are datastores and the network. I also like to think of application boot as a boundary (I don't have a really good reason for it, it just seems right); feel free to ask questions of the environment when setting up things like loggers (I'm thinking stuff like `ENV.key?(blah)` here). There are other subtle ones, but I'm not going to go over them because (1) it's good fun to work them out on your own, and (2) I'm about to cheat so hard it doesn't matter that I've left some out.

Ready for the cheating? Ok. Here it is:

You can define your own boundaries.






