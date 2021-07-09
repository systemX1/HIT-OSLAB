# lab3 实践项目∶打印进程日志

大致执行以下步骤

1. 添加fprintk()函数

   修改kernel/printk.c, 添加

2. 在建立文件描述符0,1,2(stdin,stdout,stderr)时打开日志log文件

   修改init/main.c中的    函数

3. 当发生进程状态切换时写log文件

   查找"->state"和".state"，找出改变进程状态描述的赋值语句，写入进程日志

   修改kernel/fork.c中的copy_process()函数

   修改kernel/sched.c中的wake_up()函数, sleep_on()函数, interruptible_sleep_on()函数, sys_pause()函数和schedule()函数

   修改kernel/exit.c中的do_exit()函数和sys_waitpid()函数

