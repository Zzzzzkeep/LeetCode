# No1 两个栈实现队列

​		用两个栈实现一个队列，队列的声明如下，请实现它的两个函数$appendTail$和$deleteHead$，分别完成在队列尾部插入整数和在队列头部删除整数功能。（若队列中没有元素，$deleteHead$操作返回-1）。

~~~java
class Queue{
    //成员变量
    //构造方法
    public Queue(){
  
    }
    //成员方法
    public void appendTail(int value){
        //在队列中插入一个数
    }
    public int deleteHead(){
        //在队列中删除一个数
    }
}
~~~

## 队列

​		队列是一种基于先进先出（FIFO）的数据结构，是一种只能在一端进行插入在另一端进行删除的特殊线性表，它按照先进先出的原则存在数据，先进如的数据，在读取数据时先读被读出来。

![image-20200630214102051](C:\Users\珍珍\AppData\Roaming\Typora\typora-user-images\image-20200630214102051.png)

# 思路

定义两个成员变量：$stack1$和$stack2$

$stack1$是压入数据栈

$stack2$是删除数据栈

栈的特点是先进后出

队列尾部插入数据可以直接通过$stack1$栈的push操作

```java
public void appendTail(int value){
    stack1.push(value);
}
```

删除数据操作

~~~java
public int deleteHead(){
    //判断stack2是否为空
    if(stack2.isEmpty()){
        //将stack1中的数据取出存入stack2 直到stack1为空
        while(!stack1.isEmpty){
            stack2.push(stack1.pop());
        }
       if(stack2.isEmpty()){
           return -1;
       }else{
           return stack2.pop();
       }
    }
}
~~~



