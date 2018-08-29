---
layout: default
title: About the Tech
permalink: /tech
order: 5
---

All the new experience I've gotten with new technologies over the last two terms has felt impactful enough that I believe they merit their own page.

## Linting, static code analysis, and testing  
My time here has familiarized me with some common tools to improve code quality, specifically:
* [`pylint`](https://www.pylint.org/) for linting.  
Consistent code style is something that I've always been opinionated about, but had not taken any steps towards enforcing. With a linter, my code is more cleaner and more consistent, and thus easier to read and reason about (since less effort is used processing the particulars of a given code blocks style).

* [`mypy`](http://mypy-lang.org/) for static type analysis.  
Before working at CDS I had a vague notional idea about static type analysis and how to do it with Python (via type hints), but on the EnerGuide API project that I worked on while at CDS I got exposure to actually using it.  
While I don't think it's applicable to every project/situation, it is nonetheless useful for helping to eliminate an entire class of bugs (by ensuring you're aware of exactly what kind of data you're using, what various systems expect, and knowing that they are compatible).

* [`pytest`](https://docs.pytest.org/en/latest/) for unit testing.  
Unit testing is another development practice that I had some idea about and minor exposure to preceding my time at CDS, but that the projects that I worked on solidified my understand and appreciation of.  
Interestingly my exposure was multi-level, as in the first project I was on we were building something from the ground up and emphasised our testing and in the second project I was on we were adapting an existing open source project to our needs that was without any tests, leading to quite a bit of work to verify that our changes did not introduce any regressions (ultimately leading me to an approach where I would add unit tests slowly over time to sections of the application that I touched).

_**Aside**: Another concept to mention that I didn't get to use as part of a project but I did learn about due to my work here is property based testing, and using the [`hypothesis`](https://hypothesis.works/) library to acomplish it.  
A sparse explanation of property based testing is a test framework where instead of writing hand crafted unit tests feeding known inputs and expecting known outputs, the developer writes tests that are a combination of a specification on what kind of data a given system under tests will accept, and a test that accepts such data and verifies that the system responds to it correctly._

## Continuous Integration (CI)
The above tools are great to help with local development, but by themselves don't have any leverage to ensure that the problems they were built to solve don't make their way into the codebase. Continuous integration is the tool to give the tools that leverage.

There are two competing definitions of CI, I am referring to the process of automating the build and testing of code on every change in version control. Using a CI system (We used [circleci](https://circleci.com/)) allows you to enforce that the tools I mentioned above (and any processes that you may want to do) accept your changes as correct before the change is allowed to be merged into the codebase.

Before my time at CDS I had no exposure to the process of CI, but now that I've been a part of it I cannot picture doing development without it.

## Containerization
Containerization, and [Docker](https://www.docker.com/) specifically, was a concept I had heard of before coming here, but did not have any experience with using. After learning the basic on the EnerGuide API project and continuing to learn best practices afterwards, I have come to accept it as my go-to way to deploy applications.

It allows the developer to abstract away the specifics of the infrastructure that the application will be running on, and just write code generally that will work within the container. It is a great piece of the microservice architecture puzzle.

## Container Orchestration
Once you have a set of containerized applications that are expected to coordinate with one another, a new problem arises, that of orchestration. Coordinating the set of services that a given application is built from is difficult to do manually, one has to handle configuration, scaling, communication, scheduling, and a host of other more granular details. This is extremely difficult to do yourself, and will often lead to fragile systems. That is when an Orchestration platform comes in.

There are quite a few solutions out there to this problem, but the one that I spent my time learning about while at CDS is [Kubernetes](https://kubernetes.io/), an open-source platform originally developed at Google.

## Continuous Deployment (CD)

Continuous deployment is the practice of automatically deploying new a new version of software every time a change is made to the repository that passes CI. There are many styles of doing CD, for the projects I worked on it was as simple as pushing new versions of the built Docker images (See [Containerization](#containerization)) after CI passes. The Azure product we were using to host the app was capable of detecting the new version and rolling out the changes.

However as my time at CDS was coming to a close I was helping investigate what deployment methodology/technologies would we want to invest in in the future, which ties in with the above two sections very tightly. There are lots of solutions to this problem, but after looking into the subject I've settled on a methodology if not a specific technology, [GitOps](https://www.weave.works/blog/gitops-operations-by-pull-request).

There are a few solutions trying to do the GitOps thing, but the philosophy is that the git repository is the source of truth for everything; that everything about an application is declarative instead of based on a set of instructions.
> "there are ten redis servers", rather than  "start ten redis servers, and tell me if it worked or not"

The models then is that the infrastructure currently running and the configuration in the git repository should attempt to reach convergence. Typically there is an operator, either internal or external to your system, that is responsible for monitoring the source (The git repository), and the current state, and triggering actions when there is a difference between the two.

[`weaveworks flux`](https://github.com/argoproj), [`argo`](https://github.com/argoproj/argo), and [`jenkins-x`](https://jenkins.io/projects/jenkins-x/) are the current leading solutions for this style that I encountered in my research.

While these technologies were not currently in use at CDS during my time, they are all being investigated as potential tools to augment the deployment workflow.

<div class="next-page">
    <a class="next-page-link" href="conclusions">Conclusions</a>
</div>
