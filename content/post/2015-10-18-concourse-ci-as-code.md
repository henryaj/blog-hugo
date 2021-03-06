---
title: "Concourse: CI as Code"
date: 2015-10-18T17:33:48
layout: post
category: programming
---

[Josh Hill](http://twitter.com/jamesjoshuahill) and I gave a talk at [LOPUG](http://www.meetup.com/London-PaaS-User-Group-LOPUG/) on _[Concourse](https://concourse.ci)_, our beloved continuous delivery and pipelining tool. The highlights:

  * Unlike other CI systems, Concourse puts pipelines first.
  * Everyone has a pipeline of some sort – how automated and well-documented is yours?
  * A pipeline can be a CI/CD process (build → unit → integration → deploy), but can also be used to e.g. version a resource, push code to Amazon S3 or a BOSH release, and all sorts of other things.
  * Pipelines are made of three components: [pipelines, resources and jobs](http://concourse.ci/concepts.html). Any pipeline can be described with these primitives.
  * Concourse stores your entire configuration as YAML. Nothing in the UI is configurable, which means your entire pipeline can be stored under version control, and your Concourse instance can be easily rebuilt.
  * Concourse integrates beautifully with [Cloud Foundry](https://www.cloudfoundry.org/).

The slides:

<script async class="speakerdeck-embed" data-id="be0b5c452b924571baf44bb5f68564eb" data-ratio="1.33333333333333" src="//speakerdeck.com/assets/embed.js"></script>
