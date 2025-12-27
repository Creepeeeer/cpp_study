### 块作用域（普通函数）里的static变量

**局部静态变量：只初始化一次，生命周期到程序结束**

```c++
void  f() {
	static int x = 1;
	x++;
	cout << x << endl;
}
int main() {
	for (int i = 1; i <= 10; i++)f();
}
//输出
2
3
4
5
6
7
8
9
10
11
```



### 静态全局变量和函数

**只有当前文件可以访问，你其他文件加了extern也不能访问**



#### extern用法：

都是要第一个文件定义第二个文件声明

- 变量：

第一个文件的定义+声明：

```c++
int c = 2;
```

第二个文件的声明+使用：

```c++
extern int c;
```



- 函数

第一个文件的定义+声明：

```c++
int f(int a, int b) {
	return a + b;
}   
```

第二个函数声明+使用：

```c++
extern int f(int a, int b);
```





### 类里的static

#### 静态数据成员

**属于类的整体状态不属于某个变量**

```c++
class A {
	static int a;
};
int A:: a = 2;//类内声明类外定义
//或者直接类内声明+定义
class A {
	inline static int a = 1;
};
```

#### 静态成员函数

**没有this指针只能访问类的静态变量**

```c++
class A {
public:
	inline static int a = 1;
	int b = 2;
	static void f(){
		a = 3;
		b = 4;//报错
	}
};
```

