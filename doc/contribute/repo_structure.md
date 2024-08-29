# Repositories

This document describes general structure and tools used in ProjectOrigin repositories.

## Pipeline

ProjectOrigin uses GitHub Actions for the pipeline in the repositories.

### Makefile

All repositories should have a `Makefile` that contains the targets for the pipeline.
This makefile should be used to build, test, and release the project and GitHub Actions should use this makefile
to ensure that things run locally also run in the pipeline.

The makefile enables a developer to more easily know what can be done with the project and how to do it.

The makefile also simplifies how the pipeline is written and makes it easier to run the pipeline locally.

### Renovate

ProjectOrigin uses the Renovate bot to keep dependencies up to date in the repositories.
Both nuget, github actions, protobuf and docker images are updated by the bot.

Renovate was chosen since it was able to configured to update the dependencies in a more dynamic way.


## Repository structures

Below is a overview of the structure of the most important files and directories in the repository.

```
├─.devcontainer     : Contains the configuration for the development container
├─.github           : Contains all pipeline configuration for the repository
│  ├─workflows      : Contains the workflows for the repository
│  ├─release.yml    : Contains the description of how to group the release notes based on the labels
│  └─renovate.json  : Contains the configuration for the renovate bot
├─chart             : Contains the helm chart for the project (if applicable)
├─doc               : Contains the documentation for the project
├─src               : Contains the source code for the project
│  ├─.config        : Contains the tool configuration for dotnet
│  ├─{x}.Server     : Contains the server code
│  ├─{x}.Test       : Contains the test code for the server
│  ├─Protos         : Contains the protobuf (gRPC) files for the project (if applicable)
|  └─{x}.Dockefile  : Contains the Dockerfile for the project
└─Makefile          : Contains the make targets for the project
```

### devcontainers

All repositories should have a `.devcontainer` directory that contains the configuration for the development container.
This allows developers to have a consistent development environment across different machines, and removes the "it works on my machine" problem.

The devcontainers have been developed to work with Visual Studio Code, but can be used with other IDEs as well.

The devcontainers are tested that they always work with the makefile using GitHub Actions.

### .github

The `.github` directory contains all the pipeline configuration for the repository.

Most project have 3 workflows:
- pullrequest-verify.yml: This workflow is triggered when a pull request is created or updated
  and verifies that the code compiles and the tests pass using reusable actions and the makefile.
- release-published.yml: This workflow is triggered when a release is published, builds and releases the project.
- sonarcloud.yml: This workflow is triggered when a pull request is created or updated
  and runs the SonarCloud analysis on the code.

Many of the actions use reusable actions from the [project-origin/.github](https://github.com/project-origin/.github) repository.

All references are bound using the hash of the commit, so that the actions are always stable, and are automatically updated and tested with renovate.


### chart

All projects that release a docker image should have a helm chart in the `chart` directory.
The helm chart is used to deploy the project to Kubernetes to help simplify the deployment process and provide a consistent way to deploy the project.

The helm chart should be tested with the makefile and bashscript using GitHub Actions.

### doc

The `doc` directory contains the documentation for the project - not much more to say about that.

### src

The src directory contains the source code for the project.

#### .config

The `.config` directory contains the tool configuration for dotnet if any is needed.

#### {x}.Server

Contains the server code for the project,

#### {x}.Test

