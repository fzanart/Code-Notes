# TODO:
Create simple examples for the following 3 scenarios:

- [X] Simplest version:
  A simple logger, replace prints.
- [ ] Median version
  A simple logger, writes a log file, dumps json style log.
- [ ] More complex
 Load a configuration file with log on-screen and log file + json style log.

First thing first, these are the configurable logging levels:

<div align="center">

| Level      | Numeric value |
| :---       |    :---:      |
| CRITICAL   |     50        |
| ERROR      |     40        |
| WARNING    |     30        |
| INFO       |     20        |
| DEBUG      |     10        |
| NOTSET     |      0        |

</div>

### Simplest version:
```python
import logging
logging.basicConfig(format='%(asctime)s %(message)s', datefmt='%m/%d/%Y %I:%M:%S %p', level=logging.INFO)
logging.info('is when this event was logged.')
```
Will print something like:
```
12/12/2010 11:46:36 AM is when this event was logged.
```

More on:   
[Logging facility for Python](https://docs.python.org/3/library/logging.html)  
[Logging HOWTO](https://docs.python.org/3/howto/logging.html#logging-basic-tutorial)
