## go语言基础5-数组、切片、容器

* 数组

  实例

  ```go
  var arr1 [5]int 	//定义长度为5的数组
  arr2 := [3]int{1,2,3}	//使用:时需要赋值
  arr3 := [...]int{2,3,4,5}	//可变长度
  var grid [4][5]int		//二维数组
  ```

  * 数组类型是值类型
  * 调用func f(arr [10]int) 会拷贝数组
  * go语言中一般不直接使用数组

* #### 切片(Slice)

  实例

  ```go
  arr := [...]int{0,1,2,3,4,5,6,7}
  s := arr[2:6]	//s即为切片，值为[2 3 4 5]
  //Slice的写法
  arr[2:6]= [2 3 4 5]
  arr[:6]= [0 1 2 3 4 5]
  arr[2:]= [2 3 4 5 6 7]
  arr[:]= [0 1 2 3 4 5 6 7]
  //----------------------------------------------
  //slice的扩展
  arr := [...]int{0,1,2,3,4,5,6,7}
  s1 := arr[2:6]
  s2 := s1[3:5]
  
  //s1[2,3,4,5]
  //s2[5,6]
  //s[i]不可超越len(s)，向后扩展不可超越底层数组cap(s)
  arr = [0 1 2 3 4 5 6 7]
  s1 = [2 3 4 5],len(s1) = 4, cap(s1) = 6
  s2 = [5,6],len(s2) = 2 ,cap(s2) = 3
  
  //----------------------------------------------
  //slice添加元素
  arr := [...]int{0,1,2,3,4,5,6,7}
  s1 := arr[2:6]
  s2 := s1[3:5]
  s3 := append(s2, 10)
  s4 := append(s3, 11)
  s5 := append(s4, 12)
  
  s3, s4, s5 = [5 6 10] [5 6 10 11] [5 6 10 11 12]
  arr = [0 1 2 3 4 5 6 10]
  //----------------------------------------------
  //创建  slice
  var s []int //初始值为nil
  s1 := []int{1,2,3,4}
  s2 := make([]int,16) 	//创建cap为16的slice
  s3 := make([]int, 10, 32)	//创建len=10,cap=32的slice
  
  //----------------------------------------------
  //copy  slice
  var s []int //初始值为nil
  s1 := []int{1,2,3,4}
  s2 := make([]int,16) 	//创建cap为16的slice
  s3 := make([]int, 10, 32)
  copy(s2,s1)
  //s2 = [2 4 6 8 0 0 0 0 0 0 0 0 0 0 0 0]
  
  //----------------------------------------------
  //删除元素
  //删除上面s2中的8
  s2 = append(s2[:3],s2[4:]...)
  
  //删除头元素
  front := s2[0]
  s2 = s2[1:]
  
  //删除尾元素
  tail := s2[len(s2)-1]
  s2 = s2[:len(s2)-1]
  
  ```

  slice扩容

  ```go
  func main() {
  	var s []int
  
  	for i := 0; i < 100; i++ {
  		printSlice(s)
  		s = append(s,i*2)
  	}
  
  	fmt.Println(s)
  }
  
  func printSlice(s []int)  {
  	fmt.Printf("len = %d,cap = %d\n",len(s),cap(s))
  }
  
  //--------------------输出----------------------
  len = 0,cap = 0
  len = 1,cap = 1
  len = 2,cap = 2
  len = 3,cap = 4
  len = 4,cap = 4
  len = 5,cap = 8
  len = 6,cap = 8
  len = 7,cap = 8
  len = 8,cap = 8
  len = 9,cap = 16
  。
  。
  len = 16,cap = 16
  len = 17,cap = 32
  len = 18,cap = 32
  。
  。
  len = 62,cap = 64
  len = 63,cap = 64
  len = 64,cap = 64
  len = 65,cap = 128
  len = 66,cap = 128
  len = 67,cap = 128
  。
  。
  len = 98,cap = 128
  len = 99,cap = 128
  ```

  

  * slice可以向后扩展，但不可以向前扩展
  * s[i]不可超越len(s)，向后扩展不可超越底层数组cap(s)
  * 添加元素时如果超越cap，系统会重新分配更大的底层数组
  * 由于值传递的关系，必须接收append的返回值



* #### 容器

  map实例

  ```go
  m := map[string] string {
      "name":"ai-houzi"
  }
  map[k]v
  map[k1]map[k2]v		//符合map
  m2 := make(map[string]int)	//m2 == empty map
  var m3 map[string]int	//m3 == nil
  
  ```

  * 创建：make(map[string]int)
  * 获取元素：m[key]
  * key不存在时，获得value类型的初始值
  * 用value，ok := m[key]来判断是否存在key
  * 用delete删除一个元素
  * 使用range便利key，或者遍历key, value对
  * 不保证遍历顺序，需手动对key排序
  * 使用len获得元素个数
  * map使用哈希表，必须可以比较相等
  * 除了slice, map, function的内建类型都可以作为key
  * Struts类型不包含上述字段，也可以作为key

  

