## go语言基础4-指针

```go
func swap(a, b int) {
	a, b = b, a
}
func main(){
    a ,b := 3 ,4
    swap(a,b)
    fmt.Println(a,b)//输出为3，4
}
```



```
func swap(a, b *int) {
	*a, *b = *b, *a
}

func main(){
    a ,b := 3 ,4
    swap(&a,&b)
    gmt.Println(a,b)//输出为4，3
}
```



* go语言指针不能运算
* go语言只有值传递一种方式  