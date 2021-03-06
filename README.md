# GoDataStructure

>　常見但是golang沒有內建的資料結構

- [Stack](#Stack)
- [Queue](#Queue)

## How to use

> go get github.com/skynocover/GoStackQueue

```go
package main

import (
    "fmt"
    "github.com/skynocover/GoStackQueue"
)

func main() {
    var q DataStr.Stack
    for i := 0; i < 10; i++ {
        q.Push(i)
    }
    q.Prt()
}
```

## 結構

### Queue

```go
queue.go  //使用node製作
　　node  //結點的物件
　　　　3 properties
　　　　value
　　　　prev
　　　　next
　　　　0 functions
　　Queue //list的物件
　　　　 3 properties
　　　　 head //list的頭(座標)
　　　　 rear //list的尾(座標)
　　　　 length //list長度,用來判斷此list的大小
　　　　 5 functions
　　　　 Len
　　　　 Prt
　　　　 Push
　　　　 Peek
　　　　 Get
```

### Stack

```go
stack.go  //使用array製作
　　Stack
　　　　 1 properties
　　　　 data //存放資料的陣列
　　　　 6 functions
　　　　 Len
　　　　 Prt
　　　　 Push
　　　　 Peek
　　　　 Pop
　　　　 Empty
```

## Version

### [1.0.1] 2020.06.26

#### 修正queue的bug

- queue為nil時不應該Prt

```go
func (this *Queue) Prt() {
	temp := this.head
	if this.length != 0 { //增加此判斷式
		fmt.Print(temp.value, ", ")
		for temp.next != nil {
			temp = temp.next
			fmt.Print(temp.value, ", ")
		}
	} else {
		fmt.Print(temp)
	}
	fmt.Println()
}
```

- queue在被拿光後會沒辦法push

```go
func (this *Queue) Push(value interface{}) {
	newnode := node{value, this.rear, nil}
	if this.length==0 { //利用長度判斷而不是用rear判斷,因為Get時是修改Head而不是Rear,因此用length判斷較為直觀
		this.rear = &newnode
		this.head = &newnode
	} else {
		this.rear.next = &newnode
		this.rear = &newnode
	}
	this.length++
}
```

### [1.0.0] 2020.05.01

#### ADD

- Stack
- Queue
