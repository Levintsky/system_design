# Multiprocessing

## Python Multiprocessing
- Python uses multi-process instead of multithreading for parallel;
- Difficulty:
	- For threading, easy to check a value:
```python
global val
```
	- For processes, have to apply for a queue

## Usage
- The library
```python
import multiprocessing as mp
```
- Define function:
```python
def job(q):
    res = 0
    for i in range(1000):
        res += i+i**2+i**3
    q.put(res) # queue
```
- Start and join, get return result from queue
```python
q = mp.Queue()
p1 = mp.Process(target=job, args=(q,))
p2 = mp.Process(target=job, args=(q,))
p1.start()
p2.start()
p1.join()
p2.join()
res1 = q.get()
res2 = q.get()
```
- Multi-processes share a value:
```python
v = mp.Value('i', 0)
```
- Locks:
```python
def job(v, num, l):
    l.acquire()
    for _ in range(10):
        time.sleep(0.1)
        v.value += num
        print(v.value)
    l.release()
```
- Then multiprocessing tries to modify the same shared global value. p1 getting the lock will run the whole program before releasing the resource to p2.
```python
p1 = mp.Process(target=job, args=(v, 1, l))
p2 = mp.Process(target=job, args=(v, 3, l))
p1.start()
p2.start()
p1.join()
p2.join()
```