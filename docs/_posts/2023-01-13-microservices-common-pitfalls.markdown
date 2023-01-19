---
layout: post
title:  "Common pitfalls when doing microservices"
description: This post covers some of the most common pitfalls when developing microservices.
date:   2023-01-13 16:16:33 +0100
tags: microservices opinion architecture
series: microservice-architecture
series-description: In this post I'll some pitfalls when doing microservices...
example:
---

# Overview #

You have decided that indeed microservices are the way to go for your project. You have set your eyes on a path that will accomplish the goal. You have reached the point of no
return. You should know by now that the path to microservices is riddled will pitfalls and as is the way of software development, a lot of mistakes will be made, more so when
transitioning to microservices. The way to microservices has a lot of pitfalls to avoid and most of them can not be foreseen, but few of them are common which you can plan
beforehand to avoid them. Best I can do is to at least provide you information about the most common ones, what they mean and how to avoid them.

### Plan for failure, as it is inevitable ###

Everything will fail and if we listen to Murphy (Murphy's law), it will fail at the worst possible moment. You need to plan accordingly and plan well for the failure. Requests
will fail, exceptions will happen, network will fail, hell there were few times when our cloud provider had downtime. You should bake in retries, bulkheads, idempotent consumers
and everything else you can to manage those failures. It's false to assume that everything will work as expected.

### Don't forget about the new network ###

Easier said that done, don't forget about the network. I know it sounds stupid, but when developing monoliths, no-one cares about the network, everything is packaged in a single
deployable and every method call is in the same application. With microservices, methods in the service layer will become network requests. This will introduce additional problems
which will arise after deployment and are not visible on your local development environment.

### Stopping all development on the monolith ###

Time does not stop, specifically it does not stop for your company or you clients and customers. Developing microservices will take time of course, but you should not abandon the
old monolith that's working on production, that is bringing revenue and that pays for your work. The balance hangs in the technical improvements, i.e. don't stop developing new
features, but stop wasting time on technical improvements on a project that is deprecated. You should invest time in your monolith just enough to get by, the remaining time is
the one you have to develop your microservices.

### Forgetting to add features ###

You've started your microservices project, and it will take time until it reaches the clients and customers and production environments. You can not deploy your microservices in
the middle of development and skip features that are already present in the monolith. While you develop the microservices, the monolith will also be developed and new features
will be added. Common mistake is to forget to add those features to the microservices. When you're done with developing the microservices, and they are ready for production,
recheck every feature from the monolith one by one to be sure that the clients won't miss anything.

### Making a decision beforehand and not reevaluating it when it's the time ###

Most of the development done first goes through planning phase, no matter how much time it takes. Some companies develop software with the waterfall methodology and will have
everything planned beforehand, others are agile and do a quick planning every day / week / month. The microservices will also undergo planning, but the important notion here is
that nothing is set in stone, plans can change midway, you need to adapt. Maybe something made sense when you planned the services, but now it doesn't. Don't try to break the wall,
build a door.

### Forgetting about the big picture ###

Microservices are all about the big picture. Deploy a single service, it will not function on its own, period (presumably you didn't end up with a distributed monolith). The
intricate notion of small units which do specialised work is that they together make the big picture. Think of the process as an OR operation, the surgeon alone can't execute the
operation successfully, he needs the nurses, anaesthesiologists and everyone else to work together to perform the operation. If you are developer that work on a single service,
this is not a reason to forget about all the other services in the ecosystem.

### Splitting the team to small chunks for no good reason ###

Plan your teams accordingly. There is no rule forbidding a single team working on multiple services. Additionally, this will prevent having a single person that knows the project,
which is management nightmare. Stopping all development on a service because a person is on a PTO or leaves the company is result of bad architecture and bad planning. As a rule
of thumb, if you end up with less than 3 people on a service, you should not split your team, just give your team the time to develop all the services together.

### Trying to go dynamic but still thinking static ###

Microservices are dynamic in nature as they are small parts of a bigger system. You need to have this sentence always on your mind. Adapt your mindset and start think globally
and strategically. You need to be the general of your soldiers, the architect of your microservices and that requires mind shift from you current monolithic views. Developing
microservices is not just an architecture, it's a means to provide solution for complex problems, and you should think of it that way. Every service itself can be written in
different language, in one that makes more sense, services can use the best way to communicate with each other, using REST, RPC, messaging or even something entirely different.
Use the best tools for the job, nothing says that if your monolith is written in Java, some of your microservices can't be written in NodeJS.

### Focusing too much on the technical stuff ###

Earlier in the blog I mentioned planning for failure, why it is good why should do it, but this doesn't mean that your sole goal is to manage failures and to spend all your time
developing resilient services. This means that you should do your best efforts to predict those failures but your main job as a developer is still providing value through
business logic for the customers. Every developer's dream is to work as much as possible on technical stuff, be like IronMan, but keep in mind Tony Stark had no customers for the
suits, or he would have to balance between business requirements and technical improvements. Balance is important.

### Accept that duplication will happen ###

For a good microservice architecture, you will need to have decoupling between the services. This will ease the process of integration between the services, enable different
teams to work on different services and pave the way to independence of the services. The drawback here is that more independence means more overall duplication and that is not a
bad thing. You should accept that duplication will happen on the code level and on the data level.

### Don't split up your code if it's not necessary ###

Working on multiple modules is hard, working on multiple services is even harder. Unless different teams are responsible for different services and sometimes even if this is the
case, there is no need for you to have .git repository per service as this will increase the complexity for everyday tasks. If the services are part of the same repository,
everyone can keep track of changes, compatibility problems, best practices, integrations will be easier and more importantly if a single developer is working on more than one
service will not need to have multiple IDEs open at a time which will require context switching (which is really expensive) for the developer to work on different tasks
throughout the day.

### Cross-cutting concerns ###

Don't forget about cross-cutting concerns as they will make your life a lot easier. Logging, tracing, monitoring and much more are part of these cross-cutting concerns and are
important, especially in microservice architectures as bugs and exceptions can span multiple services, request on one service can require action on another, so you will need to
have a way to track the flow in your services, monitor their health and performance and do whatever you can to find bugs more easily on production, as having bugs is guaranteed
and microservices can make them nearly impossible to find, if you don't have the right tooling of course.

### Keep track of compatibility ###

Don't forget to keep track of compatibility between different service versions. This is easily forgettable as developers tend to write the code and test it on the latest version.
One of the benefit of microservices is that you can deploy services independently. That means that inevitably there will be different versions on different environments. You need
to keep track of version compatibility (simple `excell` sheet will suffice) so dependant services will be deployed together and compatibility between services will be maintained on
environments. Non-compatible services can make a hell of their own.

### Fallacies of distributed systems ###

As microservices are distributed systems, the same rules and difficulties apply. Knowledge of distributed systems can help you a lot when designing and implementing your
microservices. The same [fallacies](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing) also apply, which are well-know for distributed systems. If you want to help
yourself and your team, print the fallacies on a paper and put them somewhere visible, so you will always be reminded of them. Some of them are mentioned in this blogpost.

### Don't reinvent the wheel ###

Don't reinvent the wheel. It's as simple as that, but I will provide at least a bit of context: There are lot tools and libraries out there which can help you in your journey.
You should focus on business logic as much as possible, not on developing a way to retry failed requests, as most of those problems are encountered by other people to, which
created tools to overcome them, such as [Smallrye Fault Tolerance](https://github.com/smallrye/smallrye-fault-tolerance)
or [Resilience4J](https://github.com/resilience4j/resilience4j). Do a quick Google or StackOverflow search before diving in code, maybe someone has thought of better solution than
you.

### Don't be scared to go back ###

Even if your plan is good, your architecture is effective, and it makes sense to you, you may be proven wrong by production environments. The chances are not everything will work
the way you want it to work. If microservices are not a good fit, don't be scared to try different architecture, or even go back to the old monolith. It takes a good developer to
accept that things are not working, and they were better before, so dust off your monolith and provide the best service to your clients and customers. Even if you end up with
distributed monolith at the end, that doesn't have to be a bad thing, it just needs to make sense for your project.

# Conclusion #

In this post I've covered most common pitfalls and problems when writing microservices. While you will encounter most of them, I hope this post will be helpful providing some
solutions and a way to avoid them. It's best to keep this points on your mind while developing and designing the system. Anticipation of the problems will help you a lot in the
design. This is the final post in this series on microservice architecture and I hope you have some take-away knowledge. 
