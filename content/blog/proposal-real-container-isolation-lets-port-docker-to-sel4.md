+++
author = "Daniil Pintjuk"
categories = ["Docker", "Cloud", "Formal Verification"]
date = "2019-08-01T22:51:31+02:00"
description = "This docker thing seams to have become a realy popular tool in the software development world. But it gives a false sence of security, \"Containerization is not Isolation\". The Sel4 micro-kernal is now formaly verified to garantee prosses isolation. Here i propose a design for a seL4 based system for running docker containers in isolation."
featured = "/2-aproaches.png"
featuredalt = ""
featuredpath = ""
linktitle = ""
title = "Proposal: Real container isolation, lets port docker to seL4  "
type = "post"

+++
1. About docker
2. About sel4
3. About need for verifiable isolation
4. Use case
5. Proposed design 1 and 2
6. Knows, unknows, learning milestones

## Normal docker:

![](img/docker model.jpg)

# Design1:

![](/img/docker on sel4 stage 1.png)

## Design2:

![](/img/docker on sel4 stage 2.png)