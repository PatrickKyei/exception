---
title: Your First Github Action
date: 2022-02-06 22:35:00 +00
categories: [Github, Flows]
tags: [github, git, technical]     # TAG names should always be lowercase
---


## Actions and Workflows

There are two components to using GitHub Actions that we'll cover:

the action itself

a workflow that uses action(s)

A workflow can contain many actions. Each action has its own purpose. We'll put the files relating to the action in their own directories.

## Types of Actions

Actions come in two types: container actions and JavaScript actions.

**Docker container actions** allow the environment to be packaged with the GitHub Actions code and can only execute in the GitHub-Hosted Linux environment.

**JavaScript actions** decouple the GitHub Actions code from the environment allowing faster execution but accepting greater dependency management responsibility.

## Step 1: Add a Dockerfile

Create a file titled action-a/Dockerfile

Create a directory action-a

Create a docker file Dockerfile

Add the following script in the Dockerfile:

FROM debian:9.5-slim

ADD entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]

The entrypoint.sh script will be run in Docker, and it will define what the action is really going to be doing.

## Step 2: Add and entrypoint script

Add the following content to the entrypoint.sh file:

## !/bin/sh -l

sh -c "echo Hello world my name is $INPUT_MY_NAME"

## Step 3: Add an action metadata file

Create a file titled action-a/action.yml

```shell
name: "Hello Actions"
description: "Greet someone"
author: "octocat@github.com"

inputs:
  MY_NAME:
    description: "Who to greet"
    required: true
    default: "World"

runs:
  using: "docker"
  image: "Dockerfile"

branding:
  icon: "mic"
  color: "purple"
```

## Step 4: Start your workflow file

Create a file titled .github/workflows/main.yml

create a workflows directory nested inside the .github directory.

In the new .github/workflows/ directory, create a file titled main.yml
Add the following content to the main.yml file:
name: A workflow for my Hello World file
on: push

## Step 5: Run an action from your workflow file

Edit .github/workflows/main.yml to append the following content:

```shell
jobs:
  build:
    name: Hello world action
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1
      - uses: ./action-a
        with:
          MY_NAME: "YourName"

          jobs: is the base component of a workflow run
```
build: is the identifier we're attaching to this job
name: is the name of the job, this is displayed on GitHub when the workflow is running
runs-on: defines the type of machine to run the job on. The machine can be either a GitHub-hosted runner or a self-hosted runner.
steps: the linear sequence of operations that make up a job
uses: actions/checkout@v1 uses a community action called checkout to allow the workflow to access the contents of the repository
uses: ./action-a provides the relative path to the action we created in the action-a directory of the repository
with: is used to specify the input variables that will be available to your action in the runtime environment. In this case, the input variable is MY_NAME, and it is currently initialized to "YourName".

Your repository now contains an action (defined in the /action-a/ folder) and a workflow (defined in the ./github/workflows/main.yml file).

This action will run any time a new commit is created or pushed to the remote repository. Since you just created a commit, the workflow should have been triggered. This might take a few minutes since it's the first time running in this repository.
