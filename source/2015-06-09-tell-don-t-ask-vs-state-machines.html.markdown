---
title: Tell Don't Ask vs. State Machines
date: 2015-06-09 01:59 UTC
tags:
---
 
# Tell Don't Ask vs. State Machines

## Sandi Metz's RailsConf 2015 "Nothing is Something"

About two nights after I came back from RailsConf 2015 in Atlanta, I got up at least 8 times and scribbled out around 10 pages of notes on removing conditionals from Rails codebases (read: my company's codebases). This sleeplessness and these notes were a side-effect of exposure to Sandi Metz's fantastic talk [Nothing is Something](https://www.youtube.com/watch?v=OMPfEXIlTVE). I'd like the missed sleep back.

You should probably watch the talk as the rationale for this post and the post itself will probably make more sense with that context.

## Tell Don't Ask (and some implications)

"Tell Don't Ask" is the idea that Metz mentions first: the avoidance of conditionals. After all, she states that they are Type Checks, the bane of Objects. So what does avoiding conditionals (and predicate/interrogator methods) mean? Well, loosely speaking, it means we can't really ask our code questions. But code still has to make decisions, right? Being of a reflection of a business process where decisions are required, doesn't our code need to make decisions too? Yes, yes it does. So, where do the decisions go?

Well, I really like the idea that we shouldn't have conditionals or decisions in our code. It makes everything wonderfully simple. But as previously mentioned, it doesn't work in non-trivial applications. So what if we try to keep conditionals and decision structures out of our business logic and domain objects? Yeah, that seems doable. This might actually work.

One of the really interesting implications of forcing decisions out of the business logic is that, to ensure the kind of smooth sailing that decisionless code would realize, the objects involved in said code would have to have to come configured from the factory with all the decisions already made. This is how real-world manufacturing actually works; your laptop doesn't ask you whether you want a wifi card everytime you boot it up, you specify that when you order it.

Hang on, that actually seems like a pretty good metaphor. What if we had some kind of object manufacturing process that preconfigured an object so that it would behave exactly as expected without being questioned about a thing as it sailed smoothly along the conveyor belt that is our business logic?

And now we come to our Rules:

## Our Rules

1. Questions *may not* be posed to objects inside business logic.
2. Questions *may* be posed to objects at the boundaries of our application.









