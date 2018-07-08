## go语言基础7-接口

实例

```go
type Retiever interface{
	Get(url string) string
}

func download(r Retiever) string {
	return r.Get("123")
}
```

#### duck typing 概念

* 像鸭子走路，像鸭子叫（长得像鸭子），那么就是鸭子
* 描述失误的外部行为而非结构
* 严格来说go属于结构化类型系统，类似**duck typing**

#### go语言中的duck typing

* 同时实现多个接口
* 同时具有python，c++的duck typing的灵活性
* 具有Java的类型检查

#### 接口

* 接口由使用者定义
* 接口的实现是隐式的
* 只要实现接口里的方法

#### 接口变量

* 接口变量自带指针
* 接口变量同意采用值传递，几乎不需要使用接口的指针
* 指针接受者实现智能以指针方式使用，值接受者都可以