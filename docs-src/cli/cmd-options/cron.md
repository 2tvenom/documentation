---
id: cron
title: temporal cron
sidebar_label: cron
description: Optional Cron Schedule for the Workflow.
tags:
  - cli reference
  - temporal cli
  - options-feature
  - command-line-interface-cli
  - cron
---

The Cron schedule can be formatted like the following:

```text
┌───────────── minute (0 - 59)
│ ┌───────────── hour (0 - 23)
│ │ ┌───────────── day of the month (1 - 31)
│ │ │ ┌───────────── month (1 - 12)
│ │ │ │ ┌───────────── day of the week (0 - 6) (Sunday to Saturday)
│ │ │ │ │
0 0 1 1 0
```
