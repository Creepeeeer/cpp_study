### cin.get

- ```c++
  int ch =cin.get();//从输入缓冲区取走一个字符包括空格 \n \t
  //返回值为int 能表示所有的unsigned char值和EOF=-1
  int ch=cin.get();
  if(ch==EOF){}
  char c=static_cast<char>(ch);
  ```

- ```c++
  cin.get(char&c);//读取一个字符存进c 
  //返回istream& 失败返回false
  ```

- ```c++
  cin.get(char*s,streamsize n);
  读取n-1个字符 遇到分隔符默认'\n‘停止 但不取走分隔符 读到的内容会以'\0'结尾
  ```



### cin.peek

**只看不取走字符**，返回值为int和EOF

```c++
int ch=cin.peek();
if(ch=='\n'){}						
```

​																										

### cin.ignore

- ```c++
  cin.ignore(count=1);//丢弃count个字符 默认参数count=1
  ```

- ```c++
  cin.ignore(count,delim)//最多丢弃count个字符，丢到delim为止(delim也会被丢)
  std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');//清到行末
  ```

  

### cin

- 跳过前导空白 （空格  \n \t)
- 读到下一个空白为止 **但不会把空白读入**



### cin.getline

```c++
cin.getline(char*,n)
//最多读n-1个字符到buf 遇到\n停止 并且会把\n移除缓冲区但不读入到buf
```



### getline

```c++
get(cin,string)//从输入流读到\n 并且会把\n丢弃
```

