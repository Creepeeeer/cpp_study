**const核心定义：修饰的对象不允许通过该名字去修改**



### 基本变量

**只读值并且必须初始化**

```c++
const int x=20;
```



### 指针

**指向常量的指针：const int*(不能修改指向对象的值，但可以指向别处）**		

```c++
int a = 1;
const int* b = &a;
//*b = 2;报错了
b = nullptr;
```



**常量指针int*const(必须初始化，只能指向一个对象，如果指向的对象不是const那么可以通过指针去修改**

```c++
	int a = 1;
	int* const b = &a;
	*b = 2;
	const int c = 2;
	//b = &c;报错
```



### 引用

**const引用可以绑定临时量延长对象生命周期**

```c++
	const string& a = "111";
	//string& a = "111";报错
```



### 函数

**返回const引用/指针：用于只读访问内部指针**

```c++
int a = 1;
int* b = &a;
const int* func() {
	return b;
}
int main() {
	//++(*(func()));报错
}
```

**成员函数后面const：const成员函数：不会修改对象状态**

```c++
class A {
public:
	int a;
	int get()const {
		return a;
	}
	void set(int x) {
		a = x;
	}
};
```



**const对象只能调用const成员函数**

```c++
	const A a;
	a.get();
	//a.set();报错
```



**const重载**

```c++
class A{
public:
	int a[10];
	int& operator[](int id) {
		cout << "调用非常量" << endl;
		return a[id];
	}
	const int& operator[](int id)const {
		cout << "调用常量" << endl;
		return a[id];
	}
};
int main() {
	A a;
	a[1];
	const A b;
	b[1];
}
```

**ps: 返回值int和const int 不构成重载，但是成员函数和const成员函数构成重载**



### **类**

**const成员变量必须用初始化列表来初始化**



**类内静态变量**

```c++
class A {
public:
    static constexpr int N = 100; // 推荐写法
};

```



### const和constexpr

const**强调只读语义**，不一定编译期可求值

constexpr**强调编译气就必须是常量**

```c++
int aa() {
	return 1;
}
const int a = aa();
constexpr int a = aa();//报错
```



### mutable

在const成员函数里也能修改

```c++
class A {
public:
	mutable int a;
	void func()const {
		a = 2;
	}
};
```

