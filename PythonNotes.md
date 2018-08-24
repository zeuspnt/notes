
## Numpy in Python print scientific notation (ex: 2.20000000e+00)
```
np.set_printoptions(suppress=True)
```
ref: [http://pythonquirks.blogspot.fr/2009/10/controlling-printing-in-numpy.html](http://pythonquirks.blogspot.fr/2009/10/controlling-printing-in-numpy.html)


## Different Means of Exiting

```os._exit():```
Exit the process without calling the cleanup handlers.

```exit(0):```
a clean exit without any errors / problems.

```exit(1):```
There was some issue / error / problem and that is why the program is exiting.

```sys.exit():```
When the system and python shuts down; it means less memory is being used after the program is run.

```quit():```
Closes the python file.

## Summary
Basically they all do the same thing, however, it also depends on what you are doing it for.

I don't think you left anything out and I would recommend getting used to quit() or exit().

You would use ```sys.exit()``` and ```os._exit()``` mainly if you are using big files or are using python to control terminal.

Otherwise mainly use ```exit()``` or ```quit()```.
