---
title: "Hello World"
date: 2021-02-25T18:58:11-08:00
draft: false
---

## What did I use to build this thing?

I may as well use this first post to discuss what I used to build the site. It'll be just a quick explanation and as a bonus, I'll talk about one snag I encountered in the deployment process.

alexlohec.com is a static site generated using [Hugo](https://gohugo.io/). Hugo is one of the most popular static site generators whose hallmarks are speed and ease of use. Easy choice.

Where to host the site was a more difficult choice in that there's an overwhelming number of options with lots of tradeoffs. I didn't end up diving too deeply into that overwhelming list, because I knew I wanted to use AWS. I use AWS in my day job and for a long running side project (more posts to come about that), so there's some synergy in using a platform I'm already familiar with and would like to keep learning more about. There may be cheaper and better options out there, but AWS checked some more important boxes for me.

And now that I've explained why I chose AWS, I can talk about the snag that had me instantly regretting that decision.

## AWS deployment snag (tl;dr "Requester pays" was enabled)

The documentation for deploying a static site using S3, which is what I elected to do, is quite good. Furthermore, there's plenty of good blog posts rehashing the same documentation, but with some more information sprinkled in. So, I was quite disappointed when I followed the official documentation for deployment and found that I received an access denied error when attempting to reach alexlohec.com. I checked and double checked all of the various access settings and got the same result. I read the aforementioned blog posts to see if they had any missing kernels from the official docs that would save me, but that just lead me down some unfortunate ACL and object-ownership rabbit holes. I hit my against the wall over a couple of days, reading and re-reading the permissions sections of my bucket, until I noticed that the "Requester pays" setting was enabled and wondered if disabling that would change anything. It did. Hallelujah.

I have no clue if that setting should be disabled by default and for some reason it was not on my bucket. If it is enabled by default I'm not sure how none of the documentation, tutorials, or forums suggested turning it off. Oh well. Hopefully, this post will fill that void and I'll save some anonymous future person a few hours someday.

Hello, world.
