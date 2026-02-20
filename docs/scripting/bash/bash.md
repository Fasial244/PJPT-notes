# Bash

These notes introduce fundamental Bash scripting concepts.  Bash is a powerful shell for automating tasks on Unix‑like systems.

## Script structure

- **Shebang:** start your scripts with `#!/bin/bash` to tell the system which interpreter to use【632795513349991†L10-L31】.
- **Make executable:** run `chmod +x script.sh` to mark a script as executable, then execute it with `./script.sh`.

## Loops

Bash provides several loop constructs.  A common pattern uses `for` to iterate over values【632795513349991†L10-L31】:

```bash
for item in 1 2 3; do
  echo "Processing $item"
done
```

You can iterate over files (`for f in *.txt; do ...`) or numeric ranges (`for ((i=0; i<10; i++)); do ...`).

## Conditionals

Use `if`, `elif` and `else` to perform conditional logic【632795513349991†L10-L31】:

```bash
if [ "$USER" = "root" ]; then
  echo "Running as root"
elif [ -f /etc/passwd ]; then
  echo "Found passwd file"
else
  echo "Condition not met"
fi
```

Square brackets denote a test; common operators include string comparisons (`=`), numeric comparisons (`-eq`, `-lt`, etc.) and file checks (`-f` for regular file, `-d` for directory, `-r` for readable, etc.).

## Echo and variables

Use `echo` to print output to the terminal【632795513349991†L10-L31】.  Variables are assigned with `name=value` and referenced using `$name`:

```bash
#!/bin/bash
greeting="Hello"
target="world"
echo "$greeting, $target!"
```

This script prints “Hello, world!”.  Combine variables, loops and conditionals to build larger automation scripts.

For further learning, consider exploring arrays, functions, error handling and subshells in the [Advanced Bash‑Scripting Guide](https://tldp.org/LDP/abs/html/).
