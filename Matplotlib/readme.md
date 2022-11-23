# Working with Matplotlib
All the basic stuff from: [Matplotlib Quick start guide][1]
### 1. Import Library:

```python
import matplotlib.pyplot as plt
```

### 2. Create figure, axes:
```python
fig, ax1 = plt.subplots()

# set fig size, more than one plot in the fig:
fig, ax = plt.subplots(2,2,figsize=(15, 15))
```
   2.1 Create secondary axis 
```python
ax2 = ax1.twinx()
```
### 3. Type of plots

   3.1 Line: ```ax.plot(x, y)```  
   3.2 Scatter  
   3.3 Bar ```ax.bar(x,y)```   

### 4. Basic colors:

### 5. Set title, axes names:
   ```python
   ax.set_title('Title')
   ax.set_xlabel('X data')
   ax.set_ylabel('Y1 data', color='g')
   ```
### 6. Plot

```
plt.show()
```


[1]: <https://matplotlib.org/stable/tutorials/introductory/quick_start.html> "quick start"
