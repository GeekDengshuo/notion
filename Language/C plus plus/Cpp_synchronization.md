### 1.Semaphore

Semaphore

信号量是最简单的一种锁

信号量分为二元信号量和多元信号量(Semaphore)

一个初始值为N的信号量，可以最多允许N个线程并发访问

信号量在整个系统中可以被任意线程获取并释放

### 2.Mutex

Mutex

互斥量类似于二元信号量，资源仅同时允许一个线程访问。
互斥量要求那个线程获取了互斥量，那个线程就要负责释放这个锁，其他线程无法去释放这个互斥量

### 3.Critical Section

临界区是比互斥量更加严格的同步手段

临界区的锁获取称为进入临界区，把锁的释放称为离开临界区

互斥量和信号量在系统的任何进程里面都是可见的，一个进程创建了一个互斥量或信号量，另一个进程试图去获取该锁是合法的。

- 临界区的作用范围仅限于本进程，其他的进程无法获取该锁