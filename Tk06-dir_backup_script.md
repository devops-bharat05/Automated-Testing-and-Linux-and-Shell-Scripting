## Task6>> Automated Backup: Write a script that compresses the /home/user/documents directory into a tarball named documents_backup.tar.gz and moves it to the /home/user/backup directory. This script should be scheduled to run daily using cron.

### Bash script that compresses the `/home/user/documents` directory into a tarball named `documents_backup.tar.gz` and moves it to the `/home/user/backup` directory. This script can be scheduled to run daily using cron.

### Script:

```bash
#!/bin/bash

# Define directories and filenames
source_dir="/home/ec2-user/documents"
backup_dir="/home/ec2-user/backup"
backup_file="documents_backup.tar.gz"

# Check if the source directory exists
if [ ! -d "$source_dir" ]; then
    echo "Error: Source directory '$source_dir' does not exist."
    exit 1
fi

# Check if the backup directory exists, create it if not
if [ ! -d "$backup_dir" ]; then
    echo "Backup directory '$backup_dir' does not exist. Creating it."
    mkdir -p "$backup_dir"
fi

# Create a tarball of the source directory
tar -czf "$backup_dir/$backup_file" -C "$source_dir" .

# Check if the tarball was created successfully
if [ $? -eq 0 ]; then
    echo "Backup successful. File created at '$backup_dir/$backup_file'."
else
    echo "Error: Backup failed."
    exit 1
fi
```

### How it works:
1. **Define Directories and Filenames**: Sets the source directory, backup directory, and backup file name.
2. **Check Source Directory**: Verifies if the source directory exists.
3. **Create Backup Directory**: Checks if the backup directory exists and creates it if necessary.
4. **Create Tarball**: Uses `tar` to compress the source directory into a `.tar.gz` file and places it in the backup directory.
5. **Check Success**: Verifies if the tarball was created successfully and prints an appropriate message.

### Scheduling with Cron:
To run this script daily, follow these steps:

1. **Save the Script**: Save the script as `dir_backup_script.sh`.
2. **Make it Executable**: Run `chmod +x /path/to/dir_backup_script.sh` to make the script executable.
3. **Edit Crontab**: Open your crontab for editing with `crontab -e`.
4. **Add Cron Job**: Add the following line to schedule the script to run daily at 2 AM:

    ```bash
    0 2 * * * /path/to/dir_backup_script.sh
    ```

    Adjust the path to where you saved the script.

This cron job will execute the backup script every day at 2 AM, compressing the documents directory and moving the backup file to the specified backup directory.
