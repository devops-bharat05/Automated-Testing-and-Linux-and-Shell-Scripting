```bash
#!/bin/bash

# Define the main directory and subdirectories
main_dir="main_directory"
sub_dirs=("sub_dir1" "sub_dir2" "sub_dir3")

# Create the main directory
mkdir -p "$main_dir"

# Loop through the subdirectories array and create each one
for sub_dir in "${sub_dirs[@]}"; do
    mkdir -p "$main_dir/$sub_dir"
done

echo "Directories created successfully!"
```

### How it works:
- `main_dir` is the main directory you want to create.
- `sub_dirs` is an array containing the names of the subdirectories you want to create inside the main directory.
- The script first creates the main directory using `mkdir -p`.
- Then, it loops through the array of subdirectories, creating each one within the main directory.

### Example Usage:
If you save this script as `create_dirs.sh`, you can run it with:

```bash
bash create_dirs.sh
```

This will create the specified directory structure.
