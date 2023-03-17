---
title: "The sad state of IPv6 in 2023"
date: 2023-02-03T09:03:20-08:00
draft: true
---

## Endless frustration with ipv6

1) My local Bulgarian ISP doesn't provision ipv6 addresses
2) github actions don't support ipv6 connections
3) docker desktop breaks when using ipv6 tunnels


## The premise

While i was doing some work for a client of mine, I needed to build some docker images and host them somewhere. Easy enough - i thought to myself - i will just create a private docker registry with [ProGet](https://inedo.com/proget) and be done with it in no time!
Easier said than done.

## Obstacle 1 - Limited IPv4

My first issue came from the already existing setup that i already have on my server.
I already have something running on port 80 & 443 on my only IPv4 Address assigned to that server (IPv4 is getting pricy!).
After some thinking, I decided to use the `/64` IPv6 network that the server had provisioned for it.

What a genius i must be!

## Obstacle 2 - No IPv6

Right after that I remembered - My ISP doesn't provision IPv6 addresses yet!