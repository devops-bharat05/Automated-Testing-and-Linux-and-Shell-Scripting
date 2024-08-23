# Task5>> File Permission Checker: Write a script that takes a file as an argument and checks if the file has read, write, and execute permissions. The script should display appropriate messages for each permission.

### Bash script that takes a file as an argument and checks its permissions. The script will display messages indicating whether the file has read, write, and execute permissions.

### Script:

```bash
#!/bin/bash

# Check if a file argument is provided
if [ "$#" -ne 1 ]; then
    echo "Usage: $0 <file>"
    exit 1
fi

# Assign the argument to a variable
file="$1"

# Check if the file exists
if [ ! -e "$file" ]; then
    echo "Error: File '$file' does not exist."
    exit 1
fi

# Check permissions and display messages
if [ -r "$file" ]; then
    echo "The file '$file' has read permission."
else
    echo "The file '$file' does not have read permission."
fi

if [ -w "$file" ]; then
    echo "The file '$file' has write permission."
else
    echo "The file '$file' does not have write permission."
fi

if [ -x "$file" ]; then
    echo "The file '$file' has execute permission."
else
    echo "The file '$file' does not have execute permission."
fi
```

### How it works:
1. **Check Argument**: The script checks if exactly one argument (the file) is provided.
2. **File Existence**: It verifies if the specified file exists.
3. **Check Permissions**: 
   - `-r` checks if the file has read permission.
   - `-w` checks if the file has write permission.
   - `-x` checks if the file has execute permission.
4. **Display Messages**: It outputs messages based on the permission checks.

### Usage:
Save the script as `file_permission_checker.sh`, make it executable with `chmod +x file_permission_checker.sh`, and run it with:

```bash
./file_permission_checker.sh /path/to/your/file
```

This script will check and display the read, write, and execute permissions for the specified file.
