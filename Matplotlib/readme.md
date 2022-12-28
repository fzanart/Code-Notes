# Working with Matplotlib
All the basic stuff from: [Matplotlib Quick start guide][1]


<p align="center">
<img src="https://user-images.githubusercontent.com/72897210/209741318-8986040a-68c3-4b5a-843f-d6b1c4f9ca54.png" />
</p>



### 1. Import Library:

```python
import matplotlib.pyplot as plt
```

### 2. Create figure, axes:
```python
fig, ax1 = plt.subplots()

# set fig size, more than one plot in the fig:
fig, axes = plt.subplots(2,2,figsize=(15, 15))

# You can also unpack the axes in the subplots call
fig, ((ax1, ax2), (ax3, ax4)) = plt.subplots(nrows=2, ncols=2, sharex=True, sharey=True)

# Or:
fig, axes = plt.subplots(nrows=2, ncols=2, sharex=True, sharey=True)
ax1, ax2, ax3, ax4 = axes.flatten()
```
   2.1 Create secondary axis 
```python
ax2 = ax1.twinx()
```
### 3. Type of plots

   3.1 Line: ```ax.plot(x, y, label='label')```  
   3.2 Scatter  
   3.3 Bar ```ax.bar(x,y, label='label')```   

### 4. Basic colors:

### 5. Set title, axes names, legend:
   ```python
   ax.set_title('Title')
   ax.set_xlabel('X data')
   ax.set_ylabel('Y1 data', color='g')
   ax.legend() # reads from label parameter
   ```
### 6. Plot

```
plt.show()
```


[1]: <https://matplotlib.org/stable/tutorials/introductory/quick_start.html> "quick start"
