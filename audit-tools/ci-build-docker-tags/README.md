# ci-build-docker-tags

## Overview

This is a tool that interrogates GitHub to determine the current docker image and tag specified in the
`/ci/build.yml` for each repo. This is useful for identifying any repos with outdated or vulnerable image versions.

It also queries the `Dockerfile.concourse` to see what image binaries are getting run on.

## Usage

### Pre-requisites

- Go installed locally
- A valid Github personal access token in an environment variable called `GITHUB_PERSONAL_ACCESS_TOKEN`

### Running the tool

Run the tool using `go run main.go`.

The tool will present a choice of teams for you to choose, or you can select your own. This will be passed in to the
code search used to identify any repositories that contain a CODEOWNERS file containing the specified string.

The tool will then identify suitable repositories and for each one will check its `/ci/build.yml` and `Dockerfile.concourse` and compile a list
of which tags of which docker images it has found. If no config is found, the image and tag columns will be left
blank in the output.
