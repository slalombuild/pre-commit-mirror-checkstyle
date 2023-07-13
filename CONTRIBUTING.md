# Contributing to `pre-commit-mirror-checkstyle`

This page is to provide sufficient material to understand the project as well as to get up to speed to start contributing.

## Pre-Reqs

### Tooling

- [java 11](https://openjdk.org/) *This repo wa created using the openjdk 11*
- [pre-commit](https://pre-commit.com/)
- [secureli](https://github.com/slalombuild/secureli) *(Optional)*

## Layout

the Pre-Commit tool offers the ability to create custom hooks, as well as provides multiple official *mirrors* of other repos and tools. This repo provides a mirror for the [checkstyle](https://checkstyle.sourceforge.io/) linter, a popular `java` linter.

### Shell Language

This hook utilizes shell scripting (bash) since java is not a support language (environment) for out-of-box pre-commit. The script ensures the necessary `jar` files and configs are locally downloaded first. Then utilizes the host `java` implementaion to run the linter on the identified java files.

### `.scripts`

`checkstyle-pre-commit.sh` is the entry point when the `checkstyle-java` hook is executed. This shell scripts acts as both a wrapper for checkstyle and parses the output to determine whether the hook failed or passed.

### `.pre-commit-hooks.yaml`

When pre-commit pulls in the repo to use for the hook, it searches for the `.pre-commit-hooks.yaml` file at the root of the repo to identifiy available hooks, and how to execute them. More info can be found: [Creating New Hooks](https://pre-commit.com/#new-hooks).

## Publishing

In order for changes to be pulled in and tested against in an other repo that utlizes pre-commit, a ***new Releas must be created in github***. These release are set using github's standard versioning syntax (i.e. v1.1.1). These release versions are then referenced in the secondary repo by updating the `rev` field for the hook configuration in the `.pre-commit-config.yaml`.

Happy Coding!
