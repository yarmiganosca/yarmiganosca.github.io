---
title: Tell Don't Ask vs. State Machines
date: 2015-06-09 01:59 UTC
published: false
tags:
---
 
# Tell Don't Ask vs. State Machines

Disclaimer: when I'm talking about workflows and state machines, I'm specifically talking the kinds of formally defined workflows that gems like [State Machine](http://github.com/pluginaweek/state_machine), [AASM](http://github.com/aasm/aasm), and [Statesman](http://github.com/gocardless/statesman).

So this all started with [this post](PUT LINK HERE). I'm not really going to recap the motivations for this post other than to say trying to remove conditionals from Business Logic State Machines (aka Workflows) seems like a really interesting problem that could result in interesting design(s). Also, from here on in, I'm going to be talking about Workflows instead of State Machines; some of the observations I make relate state in the State Machine to internal object state, and those sentences get easier to both write and read if I can talk about workflow position instead of State Machine state. So that's what I'm going to do.

## (ActiveRecord's) Callbacks (that contain Business Logic) are Bad

1. Callbacks delinearize Business Logic
2. 


## Formally Defined Workflows are Bad

1. They use ActiveRecord callbacks.
2. You can have the callback for one transition invoke another one. This expressly breaks with the simluationist tendencies in object design, as "the system" is invoking that second transition; user objects (note I didn't say "users") should be the only things that can invoke workflow transitions, as a simulation of the domain with objects would indicate.
3. Position in a workflow is **not** core to a participant object's identity and composition. Whether an order is paid for or returned has no effect on its order-ness. I personally don't think any state or status column belongs in the object's table representation, but pragatism dictates I soften that extremism.
4. Workflow transitions should be descriptive, not prescriptive. Position in a workflow should be determined by the object's internal state, not the other way around. Saying explicitly in code "when you transition from A to B, do X" is very strange and backwards. It should be "given that you were in A and did X, you are now in B".


We will need to specialize The Rules from the other post to get Workflow-specific Rules. First the Rules unspecialized:

## The (Abstract) Rules

1. Questions **may not** be posed to objects inside business logic.
2. Questions **may** be posed to objects at the boundaries of our application.

And here's what I've come up with:

## The Rules for Workflows

1. Questions **may not** be posed to objects inside business log.
1a. Objects involved in the Workflow **may not** be asked what their workflow position is.


Also, although there are many types of boundaries, the only one we're going to be concerned with here is the database, since that's were workflow position (or 'state', though why I'm not using that term to mean this concept will become apparent) information typically resides.

## The Problem of State Machines


