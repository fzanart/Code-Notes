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

### Median version:

Filename specifies that a FileHandler be created, using the specified filename, rather than a StreamHandler.
If filename is specified, open the file in this mode. Filemode defaults to 'a'. Other options:   


| Character | Meaning |
| :---: | :--- |
| 'w' | open for writing, truncating the file first. |
| 'x' | open for exclusive creation, failing if the file already exists. |
| 'a' | open for writing, appending to the end of file if it exists. |


```python
import logging

logging.basicConfig(level=logging.INFO,
                    format="{\"time\": \"%(asctime)s\", \"levelname\": \"%(levelname)s\", \"message\": \"%(message)s\"},",
                    datefmt='%m/%d/%Y %I:%M:%S %p',
                    filename='log_file.log',
                    filemode='x')
```

### More complex: work in progress

*logging.setLogRecordFactory(factory)
Set a callable which is used to create a LogRecord.*  
Have a look at:    
https://stackoverflow.com/a/67953106/15504210   
https://docs.python.org/3/library/logging.html#logging.setLogRecordFactory   


```python
import logging

# set up logging to file - see previous section for more details
logging.basicConfig(level=logging.DEBUG,
                    format='%(asctime)s %(name)-12s %(levelname)-8s %(message)s',
                    datefmt='%m-%d %H:%M',
                    filename='/tmp/myapp.log',
                    filemode='w')
# define a Handler which writes INFO messages or higher to the sys.stderr
console = logging.StreamHandler()
console.setLevel(logging.INFO)
# set a format which is simpler for console use
formatter = logging.Formatter('%(name)-12s: %(levelname)-8s %(message)s')
# tell the handler to use this format
console.setFormatter(formatter)
# add the handler to the root logger
logging.getLogger('').addHandler(console)

# Now, we can log to the root logger, or any other logger. First the root...
logging.info('Jackdaws love my big sphinx of quartz.')

# Now, define a couple of other loggers which might represent areas in your
# application:

logger1 = logging.getLogger('myapp.area1')
logger2 = logging.getLogger('myapp.area2')

logger1.debug('Quick zephyrs blow, vexing daft Jim.')
logger1.info('How quickly daft jumping zebras vex.')
logger2.warning('Jail zesty vixen who grabbed pay from quack.')
logger2.error('The five boxing wizards jump quickly.')
```


More on:   
[Logging facility for Python](https://docs.python.org/3/library/logging.html)  
[Logging HOWTO](https://docs.python.org/3/howto/logging.html#logging-basic-tutorial)  
[Logging cookbook](https://docs.python.org/3/howto/logging-cookbook.html)  
https://stackoverflow.com/questions/50144628/python-logging-into-file-as-a-dictionary-or-json  
https://stackoverflow.com/questions/48170682/can-structured-logging-be-done-with-pythons-standard-library  
