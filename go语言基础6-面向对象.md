## go语言基础6-面向对象

* #### 面向对象特点

  * go语言仅支持封装，不支持继承和多态
  * go语言没有class，只有struct 

* #### 结构体

  实例

  ```go
  type treeNode struct {
      value int
      left ,right *treeNode
  } 
  
  var root treeNode{
      root = treeNode{1,nil,nil}
      root.left = &treeNode{2,nil,nil}
      root.right = &treeNode{}
      root.right.left = new(treeNode)
  
      nodes := []treeNode{
          {3,nil,nil},
          {},
          {6,nil,&root},
  }
  ```

  ```go
  //工厂函数
  func creatTreeNode(value int) *treeNode  {
  	return &treeNode{value:value}
  }
  
  root.left.right = creatTreeNode(2)
  ```

  

  * 不论地址还是结构本身，一律使用 . 来访问成员
  * 可以使用自定义工厂函数，但注意返回了局部变量的地址！
  * 不需要知道局部变量分配到堆上还是栈上，编译器会自行判断（如果返回地址并返回，则去堆上分配，并且参与垃圾回收） 

* #### 方法

  实例

  ```go
  //定义
  func (node treeNode) print() {
  	fmt.Println(node.value)
  }
  //调用
  root.print() 
  ```

  * 显示定义和命名方法接受者
  * 只有使用指针才可以改变结构内容
  * nil指针也可以调用方法 

* #### 值接收者VS指针接收者

  * 要改变内容必须使用指针接收者
  * 结构过大也考虑使用指针接收者
  * 一致性：建议有指针接受者，最好都是指针接收者
  * 值接收者，go语言特有
  * 值/指针接收者均可以接收值/指针 

* #### 封装

  * 名字一般使用CamelCase
  * 首字母大写：public
  * 首字母小写：private

* #### 包

  * 每个目录一个包
  * main包，包含可执行入口
  * 为结构定义的方法必须放在同一个包内，可以是不同的文件
  * 可以是不同文件

  如何扩充系统类型或者别人的类型

  * 定义别名

  * 使用组合

    