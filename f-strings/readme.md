
### 1. Format thousands separators:
```python
values = 1000000
print(f'{value:,}')
```
1,000,000
### 2. Format datetime
```python
import datetime

now = datetime.datetime.now()

print(f'{now:%Y-%m-%d %H:%M}')
```
2021-08-20 15:13

### 3. Format floats (decimals):
```python
val = 12.3

print(f'{val:.2f}')
print(f'{val:.5f}')
```
12.30  
12.30000

### 4. Format width:
```python
for x in range(1, 11):
    print(f'{x:02} {x*x:3} {x*x*x:4}')
```
01   1    1  
02   4    8  
03   9   27  
04  16   64  
05  25  125  
06  36  216  
07  49  343  
08  64  512  
09  81  729  
10 100 1000  

### 5. Justify string:
```python
s1 = 'a'
s2 = 'ab'
s3 = 'abc'
s4 = 'abcd'

print(f'{s1:>10}')
print(f'{s2:>10}')
print(f'{s3:>10}')
print(f'{s4:>10}')
```

         a
        ab
       abc
      abcd
      
### 6. Format numeric notations:
```python
a = 300

# hexadecimal
print(f"{a:x}")

# octal
print(f"{a:o}")

# scientific
print(f"{a:e}")
```
12c  
454  
3.000000e+02
