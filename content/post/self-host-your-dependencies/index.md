---
title: "Safeguard Your Dependencies: Why You Should Self-Host and Your Options"
date: 2023-03-27T09:00:50+02:00
draft: false
---

## Docker hub is no more

Yes, the title is clickbaity.

As you [may have heard](https://blog.alexellis.io/docker-is-deleting-open-source-images/), Docker the company, ~~decided~~ [un-decided](https://www.docker.com/blog/no-longer-sunsetting-the-free-team-plan/) to purge open source docker hub images, unless the OSS maintainers pay them $420 a year if they want to keep their OSS images available on the hub.

Bonkers, right?  
Yes.

The unfortunate thing is, this is not the first time something like this has happened. One day everything is fine, and on the next, every DevOps person scrambles to fix broken pipelines due to a missing package like [NPM's pad-left incident](https://qz.com/646467/how-one-programmer-broke-the-internet-by-deleting-a-tiny-piece-of-code). Or NuGet/Npm/Docker/etc is down due to certificate expiration, networking outage, blown up disk and the likes. Incidents where a critical infrastructure that a major part of your company's operations depend on, stops working or is completely gone.


## YIKES!

If you are anything like me, and work at an organization big enough to be able to afford a few CPU cores and couple of terabytes of storage, you may have already thought of this situation and implemented a contingency plan or are in the works of doing so. If yes, great! You can stop reading here and work on that. BYE!

If not, please continue reading, this might save your bacon from any similar situations.

## Ok, but what should I do?

That's simple - own your dependencies (not just Docker images) and stop depending on external registries!

## Why?

Because bad things _can_ happen if you don't. You should host all your packages & dependencies regardless of the current situation with Docker hub.

What happens if `package name` disappears tomorrow like NPM's pad-left incident ?

What happens if a dependency gets re-published with malicious code under the same version?

What happens if the registry you're pulling those dependencies from goes down or you're rate limited, and your builds are broken for 6-12 hours?

What happens if you pull a dependency that has an incompatible license and you end up on the receiving end of a lawsuit?

I know, I do sound like a shill for some of the products I'm gonna list below, but I promise, I'm not.

All of these questions came from the experience of having to deal with the consequences of most of those (except the lawsuit one).

## What are my options?

Use a 3-rd party Docker registry, or package feed server where you can host your own packages & images, and all the ones you depend on.

Here's some options that might work well for you

### Option 1 - Use The cloud!

Those don't solve your problem entirely, or cover all points, but they are a start. At least you're paying and _know_ you won't loose things on a whim.

Pros

* One nice thing about the cloud options is that you can you don't have to manage the infrastructure yourself.
* Globally distributed (usually)
* Fast downloads in & out of their networks

Cons

* Cost
* May not cover all of your requirements.

---
Docker specific options

* <https://aws.amazon.com/ecr/>
* <https://azure.microsoft.com/en-us/products/container-registry>
* <https://cloud.google.com/container-registry>

Universal package registries that can host NuGet, npm, Bower, Vsix, Maven, PHP Composer, Python, Ruby Gems and the likes.

* <https://www.myget.org/>
* <https://azure.microsoft.com/en-us/products/devops/artifacts>
* <https://aws.amazon.com/codeartifact/>
* <https://cloud.google.com/artifact-registry>


### Option 2 - Self Host!

Yes, self hosting may not be the best option for your case, but at least you have the option. Also, you might _have_ to self host in some situations where external bandwidth is limited, expensive, or unreliable. One such case might be, you're located in Asia, Australia, Africa or South America.

Pros

* You OWN your infrastructure, configuration and everything
* Costs less! (usually)
* Faster transfer speeds if your build servers are also on premise.

Cons

* You have to manage it.

Here's a couple of options that you can self host.

* <https://inedo.com/proget>
* <https://jfrog.com/artifactory/>

My personal pick is Inedo's ProGet, since it's free for commercial use, and you have to pay only for the advanced features ( multi node support, ultra fine grained access rules), which you may or may not need, and it has a nice UI to configure everything.


## Conclusion

In conclusion, the recent events surrounding Docker hub and other incidents in the past highlight the importance of taking control of your dependencies and not solely relying on external registries. By self-hosting your dependencies or using a reliable 3rd-party Docker registry or package feed server, you can prevent disruptions to your operations and mitigate potential risks. Weigh the pros and cons of each option and choose the one that best fits your organization's needs and requirements. Remember, taking measures to own your dependencies can save you from potential headaches and ensure the smooth running of your projects.
