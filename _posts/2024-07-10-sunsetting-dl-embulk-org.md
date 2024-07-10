---
layout: posts
title: "Shutting down dl.embulk.org"
date: 2024-07-10
description: "The Embulk project has long provided redirect URLs at dl.embulk.org for downloading Embulk's executable JAR files. However, we will be shutting down dl.embulk.org, not immediately, but before too long. We plan to shut it down sometime in 2025. You'll need to download Embulk's executable JAR files directly from GitHub Releases after the shutdown. This may affect your automated installation process. Start migrating your installation process soon so that you won't be affected by this change."
author: "dmikurube"
---

In the early years, Embulk's executable JAR files were distributed from [JFrog](https://jfrog.com/)'s Bintray, but [Bintray had sunset](https://jfrog.com/blog/into-the-sunset-bintray-jcenter-gocenter-and-chartcenter/). Indeed, we've moved the location to [GitHub Releases](https://github.com/embulk/embulk/releases) before the sunset.

The Embulk project has long provided redirect URLs at `dl.embulk.org` for either Bintray or GitHub Releases. However, we will be shutting down `dl.embulk.org`, not immediately, but before too long. We plan to shut it down sometime in 2025.

You'll need to download Embulk's executable JAR files directly from [GitHub Releases](https://github.com/embulk/embulk/releases) after the shutdown. This may affect your automated installation process. Start migrating your installation process soon so you won't be affected by this change.

History
========

Let's take a quick look back at the history of `dl.embulk.org` for your interest.

Heroku
-------

Embulk hosted `dl.embulk.org` on [Heroku](https://www.heroku.com/) until 2018. We ran a simple service there to provide dynamic redirects to Bintray from `embulk-X.Y.Z.jar` and `embulk-latest.jar`, and to crawl Embulk plugins from GitHub.

You can see its repository archive at: [https://github.com/embulk/plugin-crawler](https://github.com/embulk/plugin-crawler)

We shut down the Heroku instance at the end of 2018, along with the migration to GitHub Releases from Bintray because maintaining the Heroku instance was a burden for us.

Cloudflare
-----------

The dynamic redirects of `dl.embulk.org` have been powered by [Cloudflare](https://www.cloudflare.com/)'s [Page Rules](https://developers.cloudflare.com/rules/page-rules/) since we shut down the Heroku instance, but [they announced that they were beginning its end-of-life process](https://blog.cloudflare.com/future-of-page-rules).

Their new [Rules](https://developers.cloudflare.com/rules/reference/page-rules-migration/) might cover our use-case, but we wanted to reduce the amount of things to maintain because we have limited bandwidth. It could be a good opportunity for us to revisit this. We no longer needed to provide vendor-independent stable URLs to download Embulk as [we have already deprecated the `selfupdate` sub-command in Embulk](https://www.embulk.org/articles/2023/04/13/embulk-v0.11-is-coming-soon.html#download).

Cloudflare's Page Rules migration will start in 2025. Our `dl.embulk.org` shutdown will happen almost at the same time, sometime in 2025. Please be prepared for the shutdown.
