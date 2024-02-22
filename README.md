# WaitGroup

```go
package main

import (
	"fmt"
	"sync"
)

func main() {
	var wg = sync.WaitGroup{}
	count := 5
	groupCount := 2
	wg.Add(groupCount)
	go group1(&wg, count)
	go group2(&wg, count)
	wg.Wait()
}

func group1(wg *sync.WaitGroup, n int) {
	defer wg.Done()
	for i := 0; i < n; i++ {
		fmt.Println("Sended ", i)
	}
}

func group2(wg *sync.WaitGroup, n int) {
	defer wg.Done()
	for i := 0; i < n; i++ {
		fmt.Println("Received ", i)
	}
}
```