```c++
#include<optional>//c++17
```



### 应用场景

**函数返回可能有结果也可能没结果**，如果平时整数什么的可以用-1当做无效值，但是用模版的话就不好写了



### 基本用法

#### 构造

```c++
optional<T> a;//默认无值
optional<T> b=3;//有值
optional<T> c=nullopt;//明确无值
```

#### 判空

```c++
if (a) {

}
if (a.has_value()) {

}
```

#### 取值

```c++
	int x= *a;//前提a有值否则ub
	int y = a.value();//前提有值，否则抛异常bad_optional_access
	int z = a.value_or(33);//a无值就会返回33，不会修改a的值
```

