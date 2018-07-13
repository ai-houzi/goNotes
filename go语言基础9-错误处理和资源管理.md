## go语言基础9-错误处理和资源管理

go 语言通过defer调用实现资源管理

* #### defer

  * 确保调用在函数结束时发生

* #### panic

  * 停止当前函数执行
  * 一直向上返回，执行每一层的defer
  * 如果没有遇见recover，程序会退出

* #### recover

  * 仅在defer调用中使用
  * 获取panic的值
  * 如果无法处理，可重新panic

* #### error vs panic

  * 意料之中的：使用error，如：文件打不开
  * 意料之外的：使用panic，如：数组越界