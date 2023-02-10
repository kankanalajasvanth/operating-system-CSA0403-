#include <stdio.h>
#include <unistd.h>
#define BUFFER_SIZE 10
#include <semaphore.h>
#include <pthread.h>

int buffer[BUFFER_SIZE];
int fill = 0;
int use = 0;

sem_t empty;
sem_t full;
pthread_mutex_t mutex;

void put(int value) {
    buffer[fill] = value;
    fill = (fill + 1) % BUFFER_SIZE;
}

int get() {
    int tmp = buffer[use];
    use = (use + 1) % BUFFER_SIZE;
    return tmp;
}

void *producer(void *arg) {
    int i;
    for (i = 0; i < 100; i++) {
        sem_wait(&empty);
        pthread_mutex_lock(&mutex);
        put(i);
        pthread_mutex_unlock(&mutex);
        sem_post(&full);
    }
    return NULL;
}

void *consumer(void *arg) {
    int i;
    for (i = 0; i < 100; i++) {
        sem_wait(&full);
        pthread_mutex_lock(&mutex);
        int tmp = get();
        pthread_mutex_unlock(&mutex);
        sem_post(&empty);
        printf("%d\n", tmp);
    }
    return NULL;
}

int main() {
    sem_init(&empty, 0, BUFFER_SIZE);
    sem_init(&full, 0, 0);
    pthread_mutex_init(&mutex, NULL);

    pthread_t producer_thread, consumer_thread;
    pthread_create(&producer_thread, NULL, producer, NULL);
    pthread_create(&consumer_thread, NULL, consumer, NULL);

    pthread_join(producer_thread, NULL);
    pthread_join(consumer_thread, NULL);

    sem_destroy(&empty);
    sem_destroy(&full);
    pthread_mutex_destroy(&mutex);

    return 0;
}
