+++
author = "Daniil Pintjuk"
categories = ["Cloud", "Formal Verification"]
date = "2019-08-02T00:36:02+02:00"
description = "Some sort of automated orchestration of is a must in a modern, large-scale software service  deployment.  Kubernets for example is a very popular option. Such Security and reliability are vital for an orchestration service, is a formaly verified orchestration service feasible? "
draft = true
featured = "/2019-08/orchestration.png"
featuredalt = ""
featuredpath = ""
linktitle = ""
title = "Proposal: Verifiably Secure Orchestration"
type = "post"

+++
# Introduction

Some sort of automated orchestration of is a must in a modern, large-scale software service  deployment.  Kubernets for example is a very popular option.

System administrators define declerativly the resaurces and services. The orkestration service takes care of distribuering the resources and services in order to keep all services avalable, monitoring the health of the service instances, and restarting them in case of crashes and migrating them to when resources go down.

It's vital for the orchistration service to be reliable, the reliability of the whole software service deployment relies on it. And its vital for it to be secure, a compromized manager node is in a privilaged position and could compromize the entier cluster.

This could be garanteed with a formaly verified orchestration service, functional and livelines proofs would ensure reliability.

And security properties could be proven to ensure that an uper bound on number on number of besentine managers that can be withstoud. Also a property ensuring that managers are only able to start and stop jobs runing on workers but not affect the execution of the job, or to view the data being processed by the job (is a design that ensures it even posable)

## learning milestones:

1. What the simplest posible orchestration model for formal verification
2. How should the livelines and security property are even posible to prove for such a design
3. How should this propertis be formalized?
4. What should be the target platform and language for the implementation, assembler, c, CackeML?
5. How should it be verified, thearem proving in in Hol4, or Model checking + Model driven development and mode testing of the implimentation?

A significant preestudy is needed just to answare the above questions. Such a pres-study might reveal that such a thing is not feesable.

A big problem with this project is that an orchistration service requiers ethernet access and filesystem. And we don't have formaly verified drivers for that, so it would be a big hole in the verification.