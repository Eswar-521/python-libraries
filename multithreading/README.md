## Parallel Billion Counter using Threads in Python

### Overview
This script demonstrates:
- Sequential vs. parallel computation of counting to a billion.
- Using Python's `threading` module to divide tasks across multiple threads.
- Measuring execution time for performance analysis.

---

## Python Code

```python
import datetime
from threading import Thread 
```
"""
### Sequential Billion Counter (Commented Out)
```python
c = 0
print("Seq Billion Counter Start", datetime.datetime.now())
for i in range(1000000000):
    c += 1

print(c)
print("Seq Billion Counter End", datetime.datetime.now())
```
```python
print("Parallel Billion Counter Start", datetime.datetime.now())
```
### Dictionary to store results from each thread
```python
data = {}

def count_large_num(i_thread_id, i_st, i_end):
    c = 0
    for i in range(i_st, i_end + 1):
        c += 1
    data[i_thread_id] = c
```
### Number of threads
```python
n = 5
target = 1000000000  # The number to count to
```
### Create a list to hold threads
```python
threads = []
threshold = target / n

l_st = 0
l_ed = 0
```
### Create and start n threads
```python
for threadID in range(n):
    l_st = l_ed + 1
    l_ed = l_ed + threshold

    t = Thread(target=count_large_num, args=(threadID, int(l_st), int(l_ed),))
    t.start()
    threads.append(t)
```
### Wait for all threads to complete
```python
for t in threads:
    t.join()
```
### Combine results from all threads
```python
print(data)
res = sum(data.values())

print(res)
print("Parallel Billion Counter End", datetime.datetime.now())
```








## Parallel vs. Sequential Billion Counter in Python

### Overview
This script demonstrates:
- **Sequential Counting**: A single-threaded approach.
- **Parallel Counting**: A multi-threaded approach using Python's `threading` module.
- **Performance Comparison**: Measuring start and end times.

---

## Python Code

```python
import datetime
from threading import Thread 
```
### Sequential Billion Counter
```python
today = datetime.datetime.today()
print("Start", today.strftime("%d-%b-%Y %H:%M:%S"))

a = 0
for c in range(1, 1000000001):
    a = a + 1

print(a)

today = datetime.datetime.today()
print("End", today.strftime("%d-%b-%Y %H:%M:%S"))
```
### Stats
### Start 05-Oct-2023 18:13:42
### 1000000000
### End 05-Oct-2023 18:15:00


### Parallel Billion Counter
```python
today = datetime.datetime.today()
print("Start", today.strftime("%d-%b-%Y %H:%M:%S"))
```
### Dictionary to store thread results
```python
l_thread_stats = {}

def counter_vals(p_start, p_end, p_thread):
    a = 0
    for c1 in range(p_start, p_end + 1):
        a += 1
    l_thread_stats[p_thread] = a 
```
### Creating 4 threads to divide the counting task
```python
t1 = Thread(target=counter_vals, args=(1, 250000000, 1))
t2 = Thread(target=counter_vals, args=(250000001, 500000000, 2))
t3 = Thread(target=counter_vals, args=(500000001, 750000000, 3))
t4 = Thread(target=counter_vals, args=(750000001, 1000000000, 4))
```

### Start all threads
```python
t1.start()
t2.start()
t3.start()
t4.start()
```

### Wait for all threads to finish
```python
t1.join()
t2.join()
t3.join()
t4.join()
```

### Summing up the results from all threads
```python
ctr = sum(l_thread_stats.values())

print(ctr)

today = datetime.datetime.today()
print("End", today.strftime("%d-%b-%Y %H:%M:%S"))
```
### Expected Output:
- Start 05-Oct-2023 18:27:04
- 1000000000
- End 05-Oct-2023 18:27:47










## Multi-threading in Python: Sequential vs. Parallel Execution

## Overview
This script demonstrates:
- **Sequential Execution**: Running a function one after another.
- **Parallel Execution**: Running multiple functions simultaneously using threads.
- **Dynamic Threading**: Creating and managing multiple threads dynamically.

---

## Python Code

```python
from threading import Thread 
import time
```
### Function that takes 5 seconds to execute
```python
def five_seconds_process(thread_id):
    print("ThreadID:", thread_id, "Started at:", time.time())
    for c in range(5):
        print("ThreadID:", thread_id, "Iteration Number", c+1)
        time.sleep(1)  # Pause for 1 second
    print("ThreadID:", thread_id, "Ended at:", time.time())
```
### Sequential Execution
```python
five_seconds_process(1)
five_seconds_process(2)
```
### Parallel Execution (2 Threads)
```python
t1 = Thread(target=five_seconds_process, args=(1,))
t1.start()

t2 = Thread(target=five_seconds_process, args=(2,))
t2.start()
```

### Parallel Execution with Dynamic Thread Count
```python
threads = []
print("Start")
```
### Create and start 5 threads dynamically
```python
for threadID in range(5):
    t = Thread(target=five_seconds_process, args=(threadID+1,))
    t.start()
    threads.append(t)
```
### Ensure main program waits for all threads to finish
```python
for e in threads:
    e.join()

print("End After Join")
```
















