---
layout: post
title:  "Monolith to microservices"
description: This post covers how to go about splitting a monolith to microservices.
date:   2023-01-12 16:15:33 +0100
tags: microservices opinion architecture
series: microservice-architecture
series-description: In this post I'll cover few ways to transform existing monolith to microservices...
example:
---

# Overview #

While we explored how to start new projects with microservice architecture in mind in the previous [post]({% post_url 2023-01-11-microservices-for-new-projects %}), in this post
I'll cover few of the ways to split up an existing monolith and transform it to microservices. Keep in mind that it all comes down to an individual team and specific project. There
is no silver bullet our there that will solve all your problems. You will notice that all paths I wrote are for migrating from monolith to microservices. My opinion is that for new
projects, it's better to start with a monolith or commonly known as _monolith-first_.

# Splitting up a monolith #

The most common way to migrate from monolith to microservices is to split up the monolith. This way you will reuse your existing code and will require minimal changes to the
codebase. The bad thing here is that all the bugs and workarounds from the old monolith will become part of the microservices. The split should be done in a way that you end up
with multiple standalone microservices, not a distributed monolith which is a common mistake.

### Start with non-mission-critical feature ###

Starting with non-mission-critical features will enable you and your team to harvest the experience when dealing with the most complex parts of the monolith.

### Don't forget to test everything ###

Keep your old tests, if they encompass more than one service, move them to integration tests. Keep in mind business functionality should not change, only the number of artefacts
produced by a build.

### Accept that you will fail ###

Failure should be part of the process and how you learn. The more you fail the more knowledge you gather.

### Reserve enough time ###

Splitting the whole monolith will take time, so plan it accordingly and share the information that no features will be developed for some time

### Don't forget that uptime is more important than technological change ###

You still need to maintain your monolith on production, downtime costs a lot and no technological change should divert you for keeping your uptime.

# Starting from scratch #

This is what we call a _Big Bang_ approach. Everything is done at once. You decommission your monolith and deploy your microservices all at once. You substitute your whole
application with one brush stroke. This has the benefit of getting rid of old bugs and workarounds, but main point is that you now know your domain, you have the experience to do
best effort decision and previous knowledge can help a lot in development.

### Big Bang is expensive ###

Starting from scratch will be expensive, it will cost you and your company, everyone needs to know that.

### Your monolith is your priority ###

The monolith on production is still a priority, it keeps the money coming in

### Don't start developing everything at once ###

Don't start developing all services at once. First focus on cross-cutting concerns, because they will provide the base, then focus on most isolated services

### Push ready microservices to production ###

Treat ready microservices as production ready and try to deploy them as soon as possible, as QA, customers and clients can test them early.

### Accept that things will change in meantime ###

New requirements will keep flying in and everything can change in a matter of moments.

# Hybrid path #

This migration from monolith to microservices sits someone in the middle of the previous two. The main drawback is that development is required on the monolith additional to the
development on the microservices. This will take much more time, but it's the safest route. You will get early insight in the new architecture and that insight can help you make
difficult decisions on the long run. Having more information makes the decision more informed.

### Start with non-mission-critical feature ###

Non-mission-critical features will provide a good place to learn

### Structure your project for multiple services instead of one ###

The microservices can be a different branch or a separate repository. They can even be part of the current branch and repository. Plan your structure for code re-usability and
multiple services.

### Plan accordingly to remove the feature from the monolith ###

Don't forget about developing integration points on your monolith and don't forget that removing features also takes time

### Push ready microservices to production ###

As the developed microservices will interact with the old monolith, deploy them as soon as possible and get feedback as soon as possible

### Rinse and repeat ###

Repeat the whole process as many times as needed until there is nothing left of the monolith

# Conclusion #

While there are many ways to transform your architecture from monolithic to microservices one, be careful of all the caveats while doing so and don't forget the most important
part, the monolith is what's making money for the company. It's best to plan ahead and with everyone involved, so you can make the best decision going forward. You can find more
patterns for splitting the monolith on [Martin Fowler's blog](https://martinfowler.com/articles/patterns-legacy-displacement/). In my next [post]({% post_url
2023-01-13-microservices-common-pitfalls %}) I will cover the pitfalls when doing microservices.
