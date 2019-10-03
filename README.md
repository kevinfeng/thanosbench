# thanosbench

[![CircleCI](https://circleci.com/gh/thanos-io/thanosbench.svg?style=svg)](https://circleci.com/gh/thanos-io/thanosbench)
[![Go Report Card](https://goreportcard.com/badge/github.com/thanos-io/thanosbench)](https://goreportcard.com/report/github.com/thanos-io/thanosbench)
[![GoDoc](https://godoc.org/github.com/thanos-io/thanosbench?status.svg)](https://godoc.org/github.com/thanos-io/thanosbench)
[![Slack](https://img.shields.io/badge/join%20slack-%23thanos-brightgreen.svg)](https://slack.cncf.io/)

Kubernetes Playground for Thanos testing &amp; benchmarking purposes 

## Available tools

See `make build && ./thanosbench --help` for available commands.
 
## Repo structure:

* cmds/thanosbench - single binary for all tools.
* config - library of mimic-style Go configurations (e.g to deploy Thanos or Prometheus on opinionated Kubernetes)
* pkg - library of non-configuration Go packages. 
* benchmarks - set of benchmarks/tests for different cases/issue/testing aimed currently for kubernetes.
  * `<benchmark name>` - directory for benchmark using [mimic](https://github.com/bwplotka/mimic) for manifests generation. See [example](/benchmarks/k8s-prometheus-remote-read)
    * gen-manifests - generated YAMLs.
    * tests - directory for all test scripts (preferable in Go).
    
TODO:
 * allow packing thanos and thanosbench binaries from certain commits into docker with ease (manual right now)
 * (?) framework for generating manifest. Right now the way is to run `go run benchmarks/<benchmark name>/main.go generate -o benchmarks/<benchmark name>/gen-manifests`
 * (?) framework for deploying those?