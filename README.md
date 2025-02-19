# Go Race Condition Example

This repository demonstrates a common race condition in Go programs involving concurrent access to a shared variable. The `bug.go` file contains the buggy code, which uses multiple goroutines to increment a counter.  The `bugSolution.go` file provides a corrected version using proper synchronization mechanisms.

## How to Reproduce

1. Clone this repository.
2. Run `go run bug.go`. Observe that the output is usually less than 1000.
3. Run `go run bugSolution.go`. Observe that the output is always 1000.

## Explanation

The race condition occurs because multiple goroutines access and modify the `count` variable concurrently without proper synchronization. This leads to unpredictable results where some increments might be lost.

## Solution

The solution uses a `sync.Mutex` to protect the `count` variable, ensuring that only one goroutine can access and modify it at a time.