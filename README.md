# Game Plan

The goal of this repository is to see if we can run different steps in a single job either serially or in parallel, based on a setting.

## Context

At work, we have a generic workflow provided by a different team. It triggers when a PR is created or changed and consists of different jobs. In it, the `verify` job needs the `build` job to finish. This is true for most of the repositories which use this workflow. However, this is not necessary for us. We can run `verify` parallel to `build`. Both the `build` and `verify` jobs create an artifact which are required as input for other jobs later on in the workflow.

## Possible Solution

I want to create a `build-and-verify` action which performs both the `build` and `verify` job in either sequential order or prallel, based on an input. It outputs both artifacts from both the `build` and `verify` jobs.
