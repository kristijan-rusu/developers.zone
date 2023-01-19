---
layout: post
title:  "When microservices are not for you"
description: This post covers when microservice architecture is not a good fit for a project.
date:   2023-01-09 16:14:33 +0100
tags: microservices opinion architecture
series: microservice-architecture
series-description: In this post I'll cover some cases when I think microservices are a bad fit for a project...
example:
---

# Overview #

Contrary to popular belief, microservices are not always a good fit, they don't solve every problem and more times than not, the effort is not warranted. I will point out few of
the cases when microservices are unnecessary complexity for you. If any of the cases fits you, you should think hard and long about doing microservices and most of the time you're
better off staying on the monolith path.

### New project ###

New projects are rarely good fit for microservices, because most of the time requirements are not clear when starting the project, the complexity of microservices and the effort to
develop them is not justified, you'd be better off with a monolith, not worrying about networks and such. Changes on a new project can be done faster in case of a monolith and
after the monolith goes in production, you will get a real feel of what is the pace of development and what are the actual technical requirements for the project. Its simple, you
don't have the actual knowledge how the system will be used and to what purpose to warrant the microservice architecture. What you can do in this case is modularize the monolith
as much as possible so when the time comes, the team is mature enough, it will be easier to migrate the existing monolith to microservices.

### DevOps can't keep up ###

One of the impotent things to keep in mind is that what developers develop, DevOps need to maintain, which often developers forget about. You create the project, write the code,
test it and when everything seems okay, you pass the project to DevOps to deploy it on production environments, monitor it and provide the best service they can. If the DevOps team
is comprises few people or the team is not as knowledgeable as the developers, they will get lost. Every issue that will rise up on production will need some developer attention.
This will also take up your time and will prevent you to work on new features, projects or improvements. DevOps needs to be comfortable maintaining the project on production. In
case you maintain the project on production, there still can be drawbacks of going microservices. Tracing and debugging production bugs will take a lot more time than it would take
with a simple monolith. Even if you adopt the Amazon way of doing microservices: 2 pizza teams and developers maintain project, this will still be a problems as you'll have more on
your plate.

### No long term goals ###

You've decided to migrate your monolithic architecture to microservices, but the company has no long-term goals for the project. This is the time to pause the migration and wait
for company decisions. If there are no long-term goals it's maybe because the company wants to deprecate the project, which will make every effort for the migration unnecessary.
Your time is expensive, so you should not waste it. It is better to spend that time with managers setting the long-term goals, your insight will be invaluable.

### No need for high availability or high performance ###

One of the biggest benefits of microservices are high availability and high performance. If the project won't have many users or need for high availability and high performance,
you're better off with monolith. Monolith is far easier to maintain and far easier to tackle simple business requirements. The chances are you are working on a project for a
specific domain, in case which the project is to be used by small group of people and doesn't require high availability. Monoliths can hold their weight and little optimisations
here and there will go a long way in serving your users with high performance without downtimes.

### Following big tech ###

Facebook, Google, Netflix, Microsoft… The big names in the IT industry are all doing microservices, but that doesn't mean you should too. If you're trying to follow in the
footsteps of big tech, you should follow all the steps. Many years of high demand pushed big tech into microservices, as monoliths can't cut it in that competition. You need to
start small and go big when there is enough demand, as all of these companies did. Jumping at the end of the hard path will have many unforeseen problems, you won't have the
maturity, resources and manpower of those companies to stand behind you in solving the difficulties.

### Going microservices just because ###

Lately in the IT industry, it seems that microservices is just one of those buzzwords that sounds fancy, your manager likes because it's what everyone is doing, your team has read
every blog there is on the internet, big tech is doing it, and it sounds modern (even on your CV). If this is the reason you are creating a microservices project, you can not be
more wrong. Don't get me wrong, the hype for microservices is justified, but it hides all the inner-workings and difficulties which you will need to overcome just for the sake
of it. What you can do in this case is just do a POC (Proof-of-concept) projects, some examples and wait for the right time to jump in the microservices water.

# Conclusion #

The architecture for a project must be chosen based on what's best for the project, not based on what's the current. My opinion is in these cases, it's best to choose the
monolith, as choosing the microservices path can lead to more roadblocks than it solves. As the architecture of a project is ever evolving, you could change that when the time
comes and everything is aligned are ready for writing microservices. In my next [post]({% post_url 2023-01-10-microservices-are-a-good-fit %}), I will share some cases when I think
microservices are the right choice. 
