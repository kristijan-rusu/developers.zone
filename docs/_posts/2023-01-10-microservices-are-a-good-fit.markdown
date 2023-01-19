---
layout: post
title:  "When microservices are a good fit"
description: This post covers cases when microservice architecture is a good fit.
date:   2023-01-10 16:14:33 +0100
tags: microservices opinion architecture
series: microservice-architecture
series-description: In this post I'll cover some cases when I think microservices are a good fit for a project...
example:
---

# Overview #

While we explored when you shouldn't do microservices in the previous [post]({% post_url 2023-01-09-microservices-are-not-for-you %}) in the series, there are cases when they are a
good fit. My opinion is that the complexity and difficulties are warranted and that you will benefit from the architecture in these few cases. There are multiple benefits of
microservices, but to reap those benefits, it must fit your needs. Every architecture has its own pros and cons, and when the pros outweigh the cons, then that's the right
architecture for your project. There actually a couple of good reasons to use the microservice architecture.

### High-availability is a must ### 

Microservices are easier to scale a lot more than a monolith. You can scale individual services which will cut down costs for the project, you can even employ AI predictions
for dynamic scaling. This will provide you with the tools to develop highly-available applications, which is a requirement in some domains. You don't want downtime on a service
for the ER or Fire department for example. You want a service that will be dynamic and will adapt to the customer and client needs as much as it can.

### High-performance is a must ###

Image you go to the ATM and you want to get some cash, what if the ATM worked such as you request your cash, it needs to process the request for a long time, so you need to come
back after three days to take your cash? Its usefulness will be a lot less than it is now. Imagine now you're working for the bank, what if someone gets cash from an ATM and his
bank balance is updated after few days? The bank will lose money as everyone will try to abuse this. Microservices can provide a way to a better performance and solution to these
issues, if you plan it right. Checking your account balance online should not affect the service for processing transactions.

### Parts of the monolith are mature enough to be standalone applications ###

This is a less common reason, but reason nonetheless. If parts of your monolith can be ported as standalone applications, it wouldn't be bad to split them out of the monolith.
This will ease up hardware requirements for customers and clients which don't use those features and will allow your company to grow, as these standalone applications can maybe
fit other needs and be deployed separately.

# Conclusion #

The architecture for a project must be chosen based on what's best for the project, not based on what's the current. My opinion is in these cases, it's best to choose the
monolith, as choosing the microservices path can lead to more roadblocks than it solves. As the architecture of a project is ever evolving, you could change that when the time
comes and everything is aligned are ready for writing microservices. In my next [post]({% post_url 2023-01-11-microservices-for-new-projects %}), I will share my opinion on how to
start new projects with microservice architecture.
