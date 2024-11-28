---
layout: posts
title: "Looking for long-term maintainers around the Embulk eco-system"
date: 2024-11-28
description: "Despite the difficult situation for an open-source community, we must say that we need your help, especially in the role of long-term maintainer, not in one-shot or short-term contributions."
author: "dmikurube"
---

The 10th anniversary of [Embulk's first release](https://github.com/embulk/embulk/releases/tag/v0.1.0) (by [@frsyuki](https://github.com/frsyuki)) is approaching. Embulk has matured, stabilized, and been used in the real world. We have also been working on modernizing Embulk, and we'd say that Embulk v1.0 is coming sooner.

[EEP-8: Milestones to Embulk v1.0, and versioning strategies to follow](https://github.com/embulk/embulk/blob/master/docs/eeps/eep-0008.md)

On the other hand, many things are indeed left behind. For example, almost all "official" plugins under [https://github.com/embulk](https://github.com/embulk) still use such old libraries (while the Embulk core, built-in plugins and utility libraries recently started using up-to-date dependency libraries). The project web-sites are not maintained so often. The user and developer documents are inadequate yet.

We have no bandwidth. Dai Mikurube ([@dmikurube](https://github.com/dmikurube)), the author of this article, is working on the open-source Embulk project in half of my working time at [Treasure Data](https://www.treasuredata.com/). What I can do are just some groundworking around the Embulk core, and appending some core architecture design documents like [EEPs](https://github.com/embulk/embulk/tree/master/docs/eeps). Hiroyuki Sato ([@hiroyuki-sato](https://github.com/hiroyuki-sato)) contributes a lot on his personal time by reviewing pull requests (from me and from outside), making suggestions, and raising issues. Hitoshi Tanaka ([@hito4t](https://github.com/hito4t)) also continues to review pull requests for JDBC-related plugins on his personal time. This is almost all of our power to maintain the Embulk eco-system today.

I have to say that the Embulk project is not sustainable enough.

The world is not easy, however
===============================

We need help. However, it is uneasy for us to say "We need **your** help" to everyone right away, unfortunately in fact.

You may remember the news about the XZ Utils backdoor that was revealed in April 2024.

* Securelist by Kaspersky: [Social engineering aspect of the XZ incident](https://securelist.com/xz-backdoor-story-part-2-social-engineering/112476/) (April 24, 2024)
* Russ Cox: [Timeline of the xz open source attack](https://research.swtch.com/xz-timeline) (April 3, 2024)

We expect that the same can happen to Embulk. Putting absolute trust in a completely new person has a risk in the world now.

In fact, we have already received a couple of "malicious-looking" contacts from some "suspicious" developers. They seemed to be leveraging generative AIs to attack a number of open-source projects. The generative AIs give attackers much more power by automatically generating more attacks, while defenders (maintainers) can only get limited help from AIs. I'd say it's a hard time for open source maintainers. (I wish AIs could perform a perfect security review and guarantee a background check!)

We need your help, still
=========================

Despite the difficult situation for an open-source community, we must say that we need your help, especially in the role of long-term maintainer, not in one-shot or short-term contributions.

Contributions are great even if they are one-shot or short-term. However, if Embulk were to receive a one-shot contribution from outside the community, the maintainers would still need to review the contribution, check that the contribution does not break compatibility, confirm that the contribution does not disturb future enhancements, and communicate with the contributor if changes need to be made to the contribution or if the contribution cannot be accepted. We do not have the bandwidth to handle this.

Here is a quote from an article about the Linux maintainers.

> To sum it up, Torvalds said, "It's one of those things where a lot of people seem to think that open source is all about programming, but a lot of it is about communication, too. Maintainers are the ones who translate. I don't necessarily mean language. I mean, the context, the reason for the code. That makes for a tough job. But, if you want to be a maintainer, trust me, there's room at the top."
>
> Steven Vaughan-Nichols: ["Linus Torvalds on the state of Linux today and how AI figures in its future"](https://www.zdnet.com/article/linus-torvalds-on-state-of-linux-today-and-how-ai-figures-in-its-future/) (Dec. 5, 2023 at 2:13 p.m. PT)

It is unrealistic for everyone to take on such a maintainer role only on their own time. Only powerful engineers can do this. If people who are supported by their organizations could take on maintainer roles, that would be ideal for sustainability.

It is unreasonable for an organization to spend its resources just on volunteers. If an organization that already uses Embulk extensively and depends on Embulk for their activities and business could support their engineers in such maintainer roles, that would be perfect for the identity of interest between the organization and the Embulk community.

It is uneasy for ourselves to invite someone who is completely new to the community, for the reason discussed above. If someone who has worked with the Embulk community can join, or introduce someone else to the maintainers, that would be straightforward for accountability.

This is not to say that we won't accept someone who is completely new, of course. However, please forgive our rudeness that we may check your background. It would be easy if you're officially supported by your organization as mentioned above.

We'd appreciate it if you and your organization would consider supporting the Embulk open-source community in this difficult time for open source.

We have some "starter projects", for you!
-------------------------------------------

Anyway, it is impossible for anyone to immediately take on such a maintainer role from ground zero for making decisions in the community.

As a starting point, we've prepared some "starter projects" for newcomers in GitHub Discussions. See: [Contributors wanted](https://github.com/orgs/embulk/discussions/categories/contributors-wanted)

If you're interested in joining as a maintainer, these are good candidates to start with. Each project would require a certain amount of work, with several decisions to be made. Let's work on them together, collaborating and discussing with us. We'd like you to expand your role in the community through the projects.

Embulk and Treasure Data, jfyi
-------------------------------

Just for your information... Some of you may have thought in the past that Embulk and the eco-system were owned and controlled by [Treasure Data](https://www.treasuredata.com/). But, that's not the case anymore! Do not hesitate to join us.

Please take a look at this article if you're interested: [Embulk maintenance goes open](https://www.embulk.org/articles/2023/03/10/embulk-maintenance-gets-open.html).
