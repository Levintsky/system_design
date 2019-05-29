# Multithreading

## Summary
- https://zhuanlan.zhihu.com/p/20953544
- http://cenalulu.github.io/python/gil-in-python/
- http://codingpy.com/article/python-201-a-tutorial-on-threads/
- https://www.jianshu.com/p/5da50563bf10
- http://www.runoob.com/python/python-multithreading.html
- https://www.cnblogs.com/fnng/p/3670789.html

## Multithreading
- The library
```python
import threading
```
- Adding threads
```python
t1 = threading.Thread(target=thread_job, name='T1')
t2 = threading.Thread(target=T2_job, name='T2')
t1.start()
t2.start()
t1.join()
t2.join()
```
-  Queue used to get return value
```python
from queue import Queue
def job(arg1, arg2, q):
	...
	q.put(result)

result = q.get()
```
- Lock
```python
def job1():
    global A, lock
    lock.acquire()
    ...
    lock.release()

def job2():
    global A, lock
    lock.acquire()
    ...
    lock.release()
```
- Then during execution:
```python
lock = threading.Lock()
A = 0
t1 = threading.Thread(target=job1)
t2 = threading.Thread(target=job2)
t1.start()
t2.start()
t1.join()
t2.join()
```
- Communication between threads? Producer-consumer mode:
```python
from queue import Queue
from threading import Thread

# A thread that produces data
def producer(out_q):
    while True:
        # Produce some data
        ...
        out_q.put(data)

# A thread that consumes data
def consumer(in_q):
    while True:
# Get some data
        data = in_q.get()
        # Process the data
        ...

# Create the shared queue and launch both threads
q = Queue()
t1 = Thread(target=consumer, args=(q,))
t2 = Thread(target=producer, args=(q,))
t1.start()
t2.start()
```
- Example 2:
```python
class worker(threading.Thread):
    def __init__(self,queue):
        threading.Thread.__init__(self)
        self.queue=queue
        self.thread_stop=False
 
    def run(self):
 	    # do something

q = Queue.Queue() # queue in the main thread

worker = worker(q)
worker.start()
# main process send tasks
q.put(["produce one cup!",1], block=True, timeout=None)
```

## Python GIL (Global Interpreter Lock)
- CPython interpreter uses GIL;
- Logic:
	- 1. Acquire GIL;
	- 2. Execute until sleep or ...;
	- 3. Release GIL;
- Only 1 GIL;
- CPU-intense tasks; (bad)
- IO-intense tasks; (good)
- Multi-core, each core has its own GIL;

## Read-Write Lock
```python

```