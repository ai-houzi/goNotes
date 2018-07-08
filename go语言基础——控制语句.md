## go语言基础——控制语句

* #### if

  

  实例

  ```go
  func method(v int) int {
      if v >100 {
          return 100
      }else if v < 0 {
          return 0
      }else {
          return v
      }
  }
  //读取文件
  func readFile(){
      const filename = "branch/abc.txt"
  	if constens, err := ioutil.ReadFile(filename); err != nil {
  		fmt.Println(err)
  	} else {
  		fmt.Printf("%s\n", constens)
  	}
  }
  ```

  

  * if 的条件里不需要括号
  * if后面可以跟多个语句
  * if条件里面可以赋值（作用域只在if语句里面）

* #### switch

  实例

  ```go
  func eval(a ,b int ,op string) int {
      var result int 
      switch op {
          case "+":
          	result = a+b
          case "-":
          	result = a-b
          case "*":
          	result = a*b
          case "/":
          	result = a/b
          default:
          	panic("不支持的类型")
      }
      return result
  }
  //没有表达式
  func grade(score int) string {
  	g := ""
  	switch {
  	case score<0||score>100:
  		panic(
  			fmt.Sprintf("Wrong score: %d",score))
  	case score<60:
  		g = "F"
  	case score<80:
  		g = "C"
  	case score<90:
  		g = "B"
  	case score<=100:
  		g = "A"
  	}
  	return g
  }
  ```

  

  * switch会自动break，除非使用fallthrough
  * switch后面可以没有表达式，在case里面加入条件即可

* #### for

  

  实例

  ```go
  sum := 0
  for i:=1;i<=100;i++{
      sum +=i
  }
  //省略初始条件
  for ; n > 0; n /= 2 {
      lsb := n % 2
      result += strconv.Itoa(lsb)
  }
  //省略结束条件
  for sacnner.Scan() {
      fmt.Println(sacnner.Text())
  }
  //省略递增表达式
  //死循环
  for {
      fmt.Println("111")
  }
  ```

  

  * for条件里不需要括号
  * for的条件里可以省略初始条件，结束条件，递增表达式