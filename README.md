# Go Race Condition Example

This repository demonstrates a race condition in Go that occurs when multiple goroutines concurrently access and modify a shared variable without proper synchronization.  The `bug.go` file contains the buggy code, while `bugSolution.go` shows how to fix it using a mutex.

## Race Condition Explanation

A race condition happens when multiple goroutines access and modify the same shared resource concurrently, and the final outcome depends on the unpredictable order in which these accesses happen. In this example, the `count` variable is shared among many goroutines.  Without proper synchronization, the increment operation (`count += i`) can be interrupted, leading to incorrect results. 

## How to Reproduce

1. Clone this repository.
2. Run `go run bug.go`.
3. Observe that the output for `count` varies on each run, highlighting the race condition.  The output is not deterministic.

## Solution

The `bugSolution.go` file demonstrates how to resolve this race condition by using a mutex (`sync.Mutex`) to ensure that only one goroutine can access and modify the `count` variable at a time. This prevents data races and ensures consistent results.