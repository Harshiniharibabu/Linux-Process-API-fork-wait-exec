# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls

```
#include <stdio.h>
#include <unistd.h>

int main() {
    pid_t pid;

    pid = fork();

    if(pid < 0) {
        printf("Fork Failed\n");
    }
    else if(pid == 0) {
        printf("CHILD PROCESS\n");
        printf("Child PID : %d\n", getpid());
        printf("Parent PID : %d\n", getppid());
    }
    else {
        printf("PARENT PROCESS\n");
        printf("Parent PID : %d\n", getpid());
        printf("Parent PID of Parent : %d\n", getppid());
    }

    return 0;
}
```

## OUTPUT


file:///home/harshinih/Documents/os/ex2.png<img width="1600" height="767" alt="image" src="https://github.com/user-attachments/assets/e5f23381-045e-4fc8-b624-3d85c0c201aa" />






## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family

```
#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <stdlib.h>

int main()
{
    pid_t pid;

    pid = fork();

    if(pid < 0)
    {
        printf("Fork failed\n");
        exit(1);
    }

    else if(pid == 0)
    {
        printf("Child Process\n");
        
        execl("/bin/ls", "ls", "-l", NULL);

        printf("Exec failed\n");
        exit(1);
    }

    else
    {
        wait(NULL);

        printf("Parent Process\n");
        printf("Child completed\n");
    }

    return 0;
}
```

## OUTPUT

file:///home/harshinih/Documents/os/ex2.2.png<img width="1693" height="941" alt="image" src="https://github.com/user-attachments/assets/a8985b58-1a06-460b-948a-85a1b125519d" />


# RESULT:
The programs are executed successfully.
