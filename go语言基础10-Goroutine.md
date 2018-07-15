## go语言基础10-Goroutine

实例

```go
func main() {
	for i := 0; i < 1000; i++ {
		go func(i int) {
			for {
				fmt.Printf("我打印的是：%d\n",i)
			}
		}(i)
	}
	time.Sleep(time.Millisecond)
}
```



#### 协程 Coroutine

* 轻量级”线程“
* 非抢占式多任务处理，由协程主动交出控制权
* 编译器/解释器/虚拟机层面的多任务
* 多个协程可能在一个或者多个线程上运行
* 子程序是协程的一个特例

#### goroutine的定义

* 任何函数只需加上go就能送给调度器运行
* 不需要在定义时区分是否是异步函数
* 调度器会在合适的店进行切换
* 使用-race来检测数据访问冲突

#### goroutine可能切换的点

* I/O，select
* channel
* 等待锁
* 函数调用（有时）
* runtime.Gosched()
* 不能保证切换，不能保证在其他地方不切换

 