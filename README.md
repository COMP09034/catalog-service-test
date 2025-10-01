<img src="./atuLogo2.jpg" height="200" align="centre"/>

# ATU Cloud Native Computing

# Lab: Build and Test Pipeline

## Lab Objectives

In this lab you'll:

## Introduction

## Getting Started

# Overview


## Installing Grype
[grype](https://github.com/anchore/grype)
```sh
curl -sSfL https://get.anchore.io/grype | sudo sh -s -- -b /usr/local/bin
```

grype .

```
comp09034@lab9PXXRG:~/lab-pipeline-commit$ grype .
 ✔ Vulnerability DB                [updated]
 ✔ Indexed file system                                                                                              .
 ✔ Cataloged contents                                cdb4ee2aea69cc6a83331bbe96dc2caa9a299d21329efb0336fc02a82e1839a8
   ├── ✔ Packages                        [0 packages]
   └── ✔ Executables                     [0 executables]
 ✔ Scanned for vulnerabilities     [0 vulnerability matches]
   ├── by severity: 0 critical, 0 high, 0 medium, 0 low, 0 negligible
   └── by status:   0 fixed, 0 not-fixed, 0 ignored [0000]  WARN no explicit name and version provided for directory source, deriving artifact
```

## Workflow
-automated process, triggered by an event
- organised into jobs that run in parallel
- each job executed on a runner instance
- permissions:
  - read to check out code
  - write to publish security events
- job composed of steps, executed sequentially
- step: 
  - action: pre-built software that can be used in a workflow for more complex tasks
  - shell command: run a shell script or command in a runner instance
  - e.g action for packaging an application into an executable, running tests, creating a docker container, pushing image to a registry
- job to carry out these steps:
  - check out source code
  - scan for vulnerabilities
  - build 
  - unit tests and integration tests
  

## Writing Workflow
[Writing Workflows](https://docs.github.com/en/actions/how-tos/write-workflows)

[Workflow Syntax](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax)

[Building and Testing Code](https://docs.github.com/en/actions/tutorials/build-and-test-code)

Actions -> Java With Gradle -> Configure
- rename to commit-stage.yml
- name: Commit Stage
- add job name Build and Test
- add security-events: write
- commit

#### View run
-> Run ./gradlew build
/home/runner/work/_temp/2bb840ff-06a1-47d4-8d58-81ed878df739.sh: line 1: ./gradlew: No such file or directory
Error: Process completed with exit code 127.


