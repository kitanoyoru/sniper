# `sniper`

[![GoDoc](https://img.shields.io/badge/api-reference-blue.svg?style=flat-square)](https://godoc.org/github.com/recoilme/sniper)

A simple and efficient thread-safe key/value store for Go.

Under the hood `sniper` uses 
[xxhash](https://github.com/cespare/xxhash).

# Getting Started

## Installing

To start using `sniper`, install Go and run `go get`:

```sh
$ go get -u github.com/recoilme/sniper
```

This will retrieve the library.

## Usage

The `Sniper` includes this methods:
`Set`, `Get`, `Incr`, `Decr`, `Delete`, `Count`, `Open`, `Close`, `FileSize`, `Backup`.

```go
s, _ := Open("1")
s.Set([]byte("hello"), []byte("go"))
res, _ = s.Get([]byte("hello"))
fmt.Println(res)
s.Close()
// Output:
// go
```

## Performance

Benchmarking conncurrent SET, GET, DELETE operations vs github.com/dgraph-io/badger v1.6.0

```
go version go1.13 darwin/amd64 (Macbook Early 2015)

     number of cpus: 4
     number of keys: 1000000
            keysize: 10
        random seed: 1569597566903802000

-- sniper --

set: 1,000,000 ops over 4 threads in 4983ms, 200,681/sec, 4983 ns/op, 69.3 MB, 72 bytes/op
get: 1,000,000 ops over 4 threads in 2000ms, 500,099/sec, 1999 ns/op, 7.6 MB, 8 bytes/op
del: 1,000,000 ops over 4 threads in 4689ms, 213,281/sec, 4688 ns/op, 33.5 MB, 35 bytes/op

-- badger --

set: 1,000,000 ops over 4 threads in 25331ms, 39,476/sec, 25331 ns/op, 121.0 MB, 126 bytes/op
get: 1,000,000 ops over 4 threads in 2222ms, 450,007/sec, 2222 ns/op, 53.9 MB, 56 bytes/op
del: 1,000,000 ops over 4 threads in 25292ms, 39,538/sec, 25291 ns/op, 42.2 MB, 44 bytes/op

```

## Contact

Vadim Kulibaba [@recoilme](https://github.com/recoilme)

## License

`sniper` source code is available under the MIT [License](/LICENSE).