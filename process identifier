#include <stdio.h>
#include <unistd.h>

int main() 
  {
  pid_t pid, ppid;  
  if (pid == -1) {
    perror("Fork failed");
    return 1;
  } else if (pid == 0) {
    
    printf("I am the child process.\n");
    pid = getpid();  
    pid = getpid();  
    printf("Child PID: %d\n", pid);
    printf("Parent PID: %d\n", ppid);
  } else {
    
    printf("I am the parent process.\n");
    pid = getpid();  
    printf("Parent PID: %d\n", pid);
  }
  
  return 0;
}
