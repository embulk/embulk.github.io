---
layout: posts
title: "dl.embulk.org is shutting down"
date: 2025-03-27
description: "As we announced months ago, we are shutting down dl.embulk.org."
author: "dmikurube"
---

As we announced months ago in "[Shutting down dl.embulk.org](https://www.embulk.org/articles/2024/07/10/sunsetting-dl-embulk-org.html)", we are shutting down `dl.embulk.org`.

Current Status
===============

As of March 27, 2025, URLs like `https://dl.embulk.org/embulk-X.Y.Z.jar` and `https://dl.embulk.org/embulk-latest.jar` are already returning the `404 File not found` error. If you reply on these URLs, especially in your automated deployment mechanism, change them to download from [GitHub Releases](https://github.com/embulk/embulk/releases) now.

The top page [`https://dl.embulk.org/`](https://dl.embulk.org/) is available to display some information about the shutdown and to direct you to download the packages from [GitHub Releases](https://github.com/embulk/embulk/releases).

This top page and the domain name `dl.embulk.org` will still remain for a while, but may be discontinued in the future.
