# buildkite-go [![GoDoc](https://img.shields.io/badge/godoc-Reference-brightgreen.svg?style=flat)](http://godoc.org/github.com/buildkite/go-buildkite) [![Build status](https://badge.buildkite.com/b16a0d730b8732a1cfba06068f8450aa7cc4b2cf40eb6e6717.svg?branch=master)](https://buildkite.com/buildkite/go-buildkite)

A [Go](http://golang.org) library and client for the [Buildkite API](https://buildkite.com/docs/api). This project draws a lot of it's structure and testing methods from [go-github](https://github.com/google/go-github).

# Usage

To get the package, execute:

```
go get github.com/buildkite/go-buildkite/v3/buildkite
```

Simple shortened example for listing all pipelines is provided below, see examples for more.

```go
import (
    "github.com/buildkite/go-buildkite/v3/buildkite"
)
...

config, err := buildkite.NewTokenConfig(*apiToken, false)

if err != nil {
	log.Fatalf("client config failed: %s", err)
}

client := buildkite.NewClient(config.Client())

pipelines, _, err := client.Pipelines.List(*org, nil)

```

Note: not everything in the API is present here just yet—if you need something please make an issue or submit a pull request.

# Releasing

1. Update the version number in `version.go`
2. Generate a changelog using [ghch](https://github.com/Songmu/ghch): `ghch --format=markdown --next-version=v<next-version-number>`, and update it in `CHANGELOG.md`
3. Commit and tag the new version
4. Create a matching [GitHub release](https://github.com/buildkite/go-buildkite/releases)

# License

This library is distributed under the BSD-style license found in the LICENSE file.
