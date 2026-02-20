# Python

These are introductory Python notes captured from your course.

## Running scripts in the background

To run a script without blocking the terminal, append an ampersand (`&`) at the end of the command:

```bash
python3 script.py &
```

This executes `script.py` in the background so you can continue using the shell【970648312746439†L11-L18】.

## Reading files

Python’s `open()` function returns a file object.  Use `read()` or `readline()` to extract content, then close the file when done:

```python
# read entire file into one string
with open('file.txt', 'r') as f:
    data = f.read()

# read a single line
with open('file.txt', 'r') as f:
    first_line = f.readline()

# manual open/close
f = open('file.txt')
contents = f.read()
f.close()  # remember to close the file【970648312746439†L11-L18】
```

The `with` context manager automatically closes the file, which is preferred.  These operations are useful when writing scripts to parse output or logs during penetration tests.
