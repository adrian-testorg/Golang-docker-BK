# Buildkite test go project

[![Go Reference](https://pkg.go.dev/badge/golang.org/x/example.svg)](https://pkg.go.dev/golang.org/x/example)

This repository is a fork of a basic Golang example repo, trimmed down to contain a single example. It contains a simple CI process on [buildkite.com](https://buildkite.com/home) which takes an input from the user and outputs the user's name.

## Locally build the project

```
$ git clone https://github.com/adrian-testorg/Golang-docker-BK.git
$ cd hello
$ go build
```
A simple Go application that takes a command line argument, and then returns it to you in a string:

```
$ chmod +x hello/hello
$ ./hello/hello John Doe
```

The above will return 'Hello, John Doe!'

### Buildkite Setup

### Agents
Buildkite offers hosted agents for you to builds. Have a look [here](https://buildkite.com/docs/pipelines/hosted-agents/overview). Within this build, a linux hosted agent was leveraged.

### How the pipeline works

![image](https://github.com/user-attachments/assets/00feb1e4-17f7-401c-a196-209ada9ea63b)

1. Buildkite performs a pipeline upload function which uploads ./buildkite/pipeline.yml to buildkite to run(don't need to include any code)
2. Go application runs the build, creates the artifact and uploads it to [Buildkite Artifacts](https://buildkite.com/docs/pipelines/artifacts)
3. A manual approval check is required and a prompt appears to ask a user for the input
4. Downloads artifacts and executes go binary

### Recommendations on making it production ready

1. Include a vulnerability scan of the code
2. Ensure only specified personnal can approve the progress
3. Don't EVER EVER build on main like me.....
4. Leverage [buildkite packages](https://buildkite.com/packages) for artifact storage

