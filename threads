#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

void *thread_function(void *arg)
{
    int i;

    for (i = 0; i < 10; i++) {
        printf("Thread says %d\n", i);
        sleep(1);
    }

    pthread_exit(NULL);
}

int main(void)
{
    pthread_t thread;
    int status;

    status = pthread_create(&thread, NULL, thread_function, NULL);
    if (status != 0) {
        perror("Error creating thread");
        exit(1);
    }

    status = pthread_join(thread, NULL);
    if (status != 0) {
        perror("Error joining thread");
        exit(1);
    }

    if (pthread_equal(pthread_self(), thread) != 0) {
        printf("Main thread and created thread are equal\n");
    } else {
        printf("Main thread and created thread are not equal\n");
    }

    pthread_exit(NULL);

    return 0;
}
