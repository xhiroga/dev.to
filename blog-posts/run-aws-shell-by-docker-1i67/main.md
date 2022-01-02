---
published: false
title: "Run aws-shell by docker"
cover_image: ""
description: ""
tags: aws
series:
canonical_url:
---

# TL;DR

Set this alias.

```shell
alias aws-shell='docker run --rm -it -v "$HOME/.aws:/root/.aws" hiroga/aws-shell:latest'
```

# Details

As of 2020-03-29, `aws-shell` installed by Homebrew does not work.\
To avoid the dependency problem, I run my aws-shell by docker.

Dockerfile is here.\
https://github.com/hiroga-cc/docker-images/blob/master/aws-shell/Dockerfile

# Issues

It runs creating index per invoke. I want to avoid it but do not have any good
ideas.
