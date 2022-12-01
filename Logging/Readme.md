# TODO:
Create simple examples for the following 3 scenarios:

- [X] Simplest version:
  A simple logger, replace prints.
- [ ] Median version
  A simple logger, writes a log file, dumps json style log.
- [ ] More complex
 Load a configuration file with log on-screen and log file + json style log.

First thing first, these are the configurable logging levels and their applicability:

<div align="center">

| Level      | Numeric value | When it’s used |
| :---       |    :---:      | :--- |
| CRITICAL   |     50        | A serious error, indicating that the program itself may be unable to continue running. |
| ERROR      |     40        | Due to a more serious problem, the software has not been able to perform some function. |
| WARNING    |     30        | An indication that something unexpected happened, or indicative of some problem in the near future (e.g. ‘disk space low’). The software is still working as expected. |
| INFO       |     20        | Confirmation that things are working as expected. |
| DEBUG      |     10        | Detailed information, typically of interest only when diagnosing problems. |
| NOTSET     |      0        |

</div>

### Simplest version:
```python
import logging
logging.basicConfig(format='%(asctime)s %(levelname)s %(message)s', datefmt='%m/%d/%Y %I:%M:%S %p', level=logging.INFO)
logging.info('is when this event was logged.')
```
Will print something like:
```
12/12/2010 11:46:36 AM INFO is when this event was logged.
```

More on:   
[Logging facility for Python](https://docs.python.org/3/library/logging.html)  
[Logging HOWTO](https://docs.python.org/3/howto/logging.html#logging-basic-tutorial)
