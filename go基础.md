## go语言基础——变量

* #### 定义变量类型

  * 使用var关键字可放在函数内，或直接放在包内
  * 可以使用var()，集中定义变量
  * 编译器可以自动决定类型
  * ：=可以使代码短一些，但只能在函数中使用
  * 函数外面定义变量必须有var、func等关键字

  ```go
  // 前变量后类型
  var a string   	//值为“”
  var b int		//值为0
  var a string = "123"
  
  //直接定义，自动决定类型
  var a,b,c = 3,4,true
  //冒号定义
  a,b,c :=3,4,true
  
  ```

   

* #### 内建变量类型

  * bool ,string
  * (u)int, (u)int8, (u)int16, (u)int32, (u)int64, uintptr
  * byte, rune
  * float32 ,float64, complex64, complex128

  go语音只有强制类型转换

  ```go
  var a,b int = 3 ,4
  var c int
  c = int(math.Sqrt(float64(a*a+b*b)))
  ```

  

* #### 常量

  const关键字

  ```go
  const filename = "123.txt"
  ```

  常量的数值可以作为各种类型使用	

  枚举类型：

  ```go
  const (
  	cpp = 1
      java = 2
      python = 3
  )
  //也可以写成自增枚举类型
  const (
  	cpp = iota
      java
      python
  )
  ```

  iota的妙用

  ```go
  const (
      b = 1<<(10 *iota) 	//1
      kb					//1024
      mb					...
      gb
      tb
  )
  ```

* #### 总结

  * 变量类型写在变量名之后
  * 编译器可推测变量类型
  * go没有char类型，只有rune
  * 原生支持复数类型