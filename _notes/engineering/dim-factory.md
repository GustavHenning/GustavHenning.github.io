---
title: Dim factory
topic: engineering
status: seed
summary: None of this text was written by AI.
started: 2026-09-12
revised: 2026-09-12
---

<aside class="definition">
  <p><dfn>dim</dfn> reduced brightness, but not completely dark.</p>
</aside>

During this year, the concept of dark factories has emerged where engineers no longer look at the code. Personally, I've used AI tools for as long as they've existed, but I haven't had the courage to completely let go of being the human in the loop at work(and I probably wont). However, I've had several pet projects where I've tried this just to infer where the industry is heading but also to see if I can improve my way of working. So what's my takeaway from all of this?

LLMs have blind spots. One of them is that they are trained using a boolean reward signal. Either you get positive feedback from the "correct" answer, or you get punished for the wrong answer. There's no one-hot encoding for "I don't know". There really should be. And datasets really should cater to this as well. There isn't a single person on earth who benefits from LLMs being confidently incorrect.

Another thing LLMs are bad at is keeping code maintainable over a long period of time. Anyone who has tried vibe coding knows that the most smooth part of it are the first few requests. The reality is that 1) Most coding isn't being written from a clean slate and 2) As the feedback loop evolves the software, it becomes increasingly hard to keep track of an updated complete requirements list given new and old, tested and greenfield.

<figure>
  <img src="{{ '/assets/images/dim-factory/harness-engineering.webp' | relative_url }}" alt="Screenshot from the talk Harness Engineering is not Enough: Why Software Factories Fail">
  <figcaption>Screenshot from the talk <a href="https://www.youtube.com/watch?v=Ib5GBkD555M">Harness Engineering is not Enough: Why Software Factories Fail</a> — Dex Horthy, HumanLayer</figcaption>
</figure>

I found myself agreeing with everything Dex said in this video, as I've also spent a significant amount of time trying to formulate similar thoughts myself. Here's what I think humans must continue to do as engineers:

<b>Eyes on the horizon.</b> Keeping a complete mental picture(<i>hint: create an actual diagram</i>) of a) what the product is today, what component it consists of and b) what the road map is, and how the diagram will change as we add these features 

<b>Maintain the critical path.</b> How do you feel about clicking on the merge button? Are you confident that production won't break if you merge this code? The answer to this question comes down to the tests in your code base. There's a lot to say about tests, and in my opinion there are a lot of tests that don't test anything, or that test your patience and ability to modify the code in a productive way. I'm gonna go out on a limb here and say that there are two kinds of useful tests:

1) End-to-end tests they tell you if you're going to regret merging this code in production. These tests are ideally as close as possible to exactly what's going to happen in production. The closer these tests are to actual production, the more useful they are. 

2) Fast sanity checking tests. I don't want to say unit tests. It's easy to write tests that make it hard to change the code. It takes effort to write great unit tests. There is however a good reason to have a number of tests that run in under one second, that enforce the contract and the mental model that the engineers have about the truths in the code base. These tests either give you direction or they tell you when a past concept and a new concept collide logically.

What's interesting is that now with agents we both write fast tests for humans but also for agents. These agentic unit tests have steering prompts in their error text. And the agentic tests also mostly don't make sense for humans. An example would be a regression test that simply assumes that the API calls won't exceed 100 ms. If the engineers theoretically come to the conclusion that this should be true then this guard rail test can steer the agents away from bad solutions. You can also have a test or a hook which fails if somebody adds a 10 line comment in the code (looking at you Claude). 

The goal is to arrive at the perfect merge request. The merge request that you want to read, that gives you the most valuable information first in its description, that proves <b>proof</b> that whatever you're trying to do works, and that discusses alternative paths and unexpected fixes that had to happen along the way. We are engineering a reading experience for the developer. A way for us to, as soon as possible, be able to tell if something should go back to the drawing board or if it's ready to merge.

The appropriate amount of human in the loop depends on what you're working on. If you're writing an internal debugger tool where you are the only consumer of it and it will never be shipped or shared with a stakeholder that is not interested in maintaining it, you might as well go for dark factory on that tool, if that makes sense. But for any software that has real consequences if it doesn't work in production it just isn't feasible to let go completely. After all, nobody has died from not being able to start Spotify.