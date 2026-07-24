# gorocksdb, a Go wrapper for RocksDB

[![GoDoc](https://godoc.org/github.com/tecbot/gorocksdb?status.svg)](http://godoc.org/github.com/tecbot/gorocksdb)

gorocksdb provides Go bindings for the RocksDB C API.

## Requirements

- Go 1.24.1 or newer
- RocksDB 6.26.1 development headers and library
- CGO enabled

RocksDB must be installed on the build machine. The package does not vendor or
build RocksDB for you.

## Install

In a Go module project:

```bash
go get github.com/tecbot/gorocksdb
```

If RocksDB is installed in a non-standard location, pass the include and library
paths through CGO:

```bash
CGO_CFLAGS="-I/path/to/rocksdb/include" \
CGO_LDFLAGS="-L/path/to/rocksdb -lrocksdb -lstdc++ -lm -lz -lbz2 -lsnappy -llz4 -lzstd" \
  go get github.com/tecbot/gorocksdb
```

When RocksDB provides a `pkg-config` file, you can inspect the required flags
with:

```bash
pkg-config --cflags --libs rocksdb
```

## Build And Test

From this repository:

```bash
go mod tidy
go build ./...
go test ./...
```

If your Go cache or module cache is not writable, set temporary cache paths:

```bash
GOPATH=/tmp/gopath GOCACHE=/tmp/gocache go test ./...
```

## Notes

This branch is adapted for RocksDB 6.26.1. Other RocksDB versions may require
small CGO signature adjustments when the upstream C API changes.

The embedded CockroachDB RocksDB is no longer supported in gorocksdb.
