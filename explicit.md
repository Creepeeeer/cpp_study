### explicit 修饰构造函数 禁止隐式转换构造

**单参数或者除了第一个参数其他参数都有默认参数(第一个参数有没有默认参数都无所谓）**

```c++
class A{
public:
	 A(int a){}
	 //explicit A(int a){}报错
};
int main() {
	A a = 1;
}
class A{
public:
	 A(int a,string b="111") {}
	 //explicit A(int a,string b="111"){}//报错
};
int main() {
	A a = 1;
}
```



### 修饰类型转换运算符，禁止隐式用户自定义转换

```c++
struct A{
	explicit operator bool() {
		return true;
	}
};
int main() {
	A a;
	bool b = a;//报错
}
```

