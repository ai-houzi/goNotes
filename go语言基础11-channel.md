## go语言基础11-channel

实例

```go
func channelDemo() {
	c := make(chan int)
	go func() {
		for {
			s := <-c
			fmt.Println(s)
		}
	}()
	c <- 1
	c <- 2
	time.Sleep(time.Millisecond)
} 
```

