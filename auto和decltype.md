### auto

#### auto x=expr;

**按值推导，丢掉引用，丢掉顶层const**

```c++
	int a = 1;
	const int b = 2;
	const int& c = 3;
	auto aa = a;
	auto bb = b;
	auto cc = c;
//aa,bb,cc类型都为int
const int*p=&a;
auto pp=p;//保留const属性
```



### auto &x=expr

**推导成引用不会丢const属性**



### auto &&x=expr

expr是左值推导成T&

expr是右值推导成T&&





### decltype

**decltype后面接括号，括号里接表达式，并且给出括号里表达式的精准推导**

```c++
int a=1;
decltype(a) b=2;
```



**双括号写法**

```c++
decltype((表达式))
```

- 表达式是左值 T&
- 表达式是将亡值 T&&
- 表达式是纯右值 T

