## go语言基础2-函数



实例

```go
//先声明方法，后定义返回类型
func eval(a, b int, op string) int {
	switch op {

	case "+":
		return a + b
	case "-":
		return a - b
	case "*":
		return a * b
	case "/":
		return a / b
	default:
		panic("方法有误")
	}
}

//带余数除法，两个返回值
func div(a, b int) (q, r int) {
	q = a / b
	r = a % b
	return
}

//函数式
func apply(op func(int, int) int, a, b int) int {
	pointer := reflect.ValueOf(op).Pointer()

	opName := runtime.FuncForPC(pointer).Name()

	fmt.Printf("calling fucntion %s with args (%d ,%d)", opName, a, b)

	return op(a, b)

}

func pow(a, b int) int {
	return int(math.Pow(float64(a), float64(b)))
}

func main() {
	fmt.Println(apply(pow, 3, 4))
    //匿名函数
	fmt.Println(
		apply(func(a int, b int) int {
			return int(math.Pow(float64(a), float64(b)))
		}, 3, 2),
	)
}

//可变参数
func sum(num ...int) int {
	s := 0
	for i := range num {
		s += num[i]
	}
	return s
}
```



	* 返回值类型写在最后面

* 函数返回多个值时可以起名字
* 仅用于简单的函数
* 对于调用者而言没有区别
* 函数可作为参数
* 没有默认参数，可选参数