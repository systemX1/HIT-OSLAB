# lab 2 添加系统调用

添加两个系统调用

```c
int iam(const char * name);
int whoami(char* name, unsigned int size);
```

需要修改*kernal/who.c, include/unistd.h*

