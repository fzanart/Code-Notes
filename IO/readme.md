### Reading all text lines striping newlines \n:

```python
whith open('path/to/file.txt', encoding='utf-8') as f:
    text_file = f.readlines()
    
text_file = [line.rstrip() for line in text_file]  
```

Alternatively:

```python
text_file = []
whith open('path/to/file.txt', encoding='utf-8') as f:
    for line in f:
        text_file.append(f.readline().rstrip())
```

Also, normaly text requiere to be splited:

```python
text_file = [line.split(' ') for line in text_file]
```
