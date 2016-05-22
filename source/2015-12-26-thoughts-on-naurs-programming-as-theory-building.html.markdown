---
title: Thoughts on Naur's "Programming as Theory Building"
date: 2015-12-26 21:34 UTC
published: false
tags:
---

I recently read Peter Naur's 1985 "Programming as Theory Building". INSERT REST OF INTRODUCTION HERE.

Naur's conception of programming as the act of building a theory to describe a domain is interesting.
It reminds me greatly of Christopher Alexander's idea of design (in general) as being a process similar to curve-fitting.
It also seem to have some overlap with Kuhn's description of scientific paradigm change (though not as much as I originally hoped).


Single Responsibility Principle: "single" differs between the bottom (construction) & the top (usage).


Design does not progress towards a specific end.
It only progresses away from.
Therefore, it only having "negative" maxims and aphorisms is appropriate.
We do not know what we want, just that we don't what "that" (for various "that"s).



Naur's concept of theory explains why when we see certain pull requests that "just don't get it", we have an emotional reaction; the author doesn't "see" the theory.
We are experiencing what Alexander would call "lack of fit", not to a design, but to a governing theory (or as the XPers call it, a system metaphor).


Does Naur assert that documentation is useless? Is it?



Are paradigms == system metaphors ? It seems possible.

Sinatra -> Vanilla Rails -> Objects on Rails.
Different projects require different paradigms.
Sinatra might be a sufficiently powerful approximation of good software design in a regime where velocity is much much smaller than the speed of light.
However, there are velocities (scales) at which the discrepancies become apparent, and we must switch to a more accurate and context-fitting design (must we? why? what is the imperative?).
When going from vanilla Rails -> Objects on Rails, does the system metaphor actually change?


Maybe Newtonian : Einsteinian is a wrong analogy.
Maybe a more accurate analogy is MVC Rails : Objects on Rails :: Point-Mass Mechanics : Continuum Mechanics .
Is an analogy here even necessary?
Do I just want to brag about all the impressive things I've read and thought about (probably a non-seperable part if I'm honest)?


Is the Red-Green-Refactor cycle of TDD similar in restrictedness to Kuhn's linear but constrained progression of 'normal science'?
No (and perhaps damning to this entire post), because the current code is not implicitly trusted to the extent that paradigms are by scientists.
Kuhn says that when an experiment fails to produce the predicted results (unless the field is already in a state of crisis), the fault will be seen to lie with the experimenter(s) and their 



Similarly, there is a scale of systems in which one doesn't need to worry about concurrency and understanding correctness in the presence of concurrency - probabilistically, you aren't likely to get transaction collisions until a certain number of simultaneous connections. Until then you can pretend (and it is quite profitable to do so) that each request is processed serially.


Kuhn's paradigm change gives credence to the adage that "the only way to build large systems is to build small systems".
If when the paradigm changes, everything has to be recast to fit into it, then having small pieces that are separate, but fit together to provide a functioning system, allows each piece to be recast into the new paradigm separately.
Having a monolith makes this kind of paradigm change massively difficult (as I've experienced firsthand).
Separating the components with interfaces may separate them from changes in each others' paradigms (Kuhn mentions changes rippling, but not very forcefully, to distant but related fields).
Exploring new theories inside a smaller component is easier simply because there is less observed data (automated tests, customer requirements) to make the new theory fit.
Also, much of the requirements to be fitted against come from the reliance other components have on the component under change.


Your dependencies are your design.
Do different system metaphors have different trouble incorporating certain dependencies or kinds of dependencies?
Is it possible to just not see certain dependencies as dependencies in certain system metaphors?
Or will they register, but as anomalies the system metaphor will struggle to describe and demonstrate the necessity of a new system metaphor?


Software practitioners may not fit Kuhn's requirements to be a scientific community.
Does this affect the applicability of his insight?
We haven't all been exposed to the same material, and certainly most of it not from texts.
What does the history of scientific education look like?
How have educators decided what to teach at what ages?

