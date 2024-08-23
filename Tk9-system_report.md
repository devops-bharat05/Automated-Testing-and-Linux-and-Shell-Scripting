# Task9 >>  System Information Report: Write a script that generates a system information report. The report should include:- System uptime - Memory usage - CPU load - Disk usage - Running processes.  The report should be saved to a file named system_report.txt.

### Bash script that generates a system information report and saves it to a file named `system_report.txt`. The report includes system uptime, memory usage, CPU load, disk usage, and running processes.

### Script:

```bash
#!/bin/bash

# Define the report file
report_file="system_report.txt"

# Generate system uptime
uptime_info=$(uptime -p)

# Generate memory usage
memory_info=$(free -h)

# Generate CPU load
cpu_load=$(uptime | awk -F'load average:' '{ print $2 }' | sed 's/,//g')

# Generate disk usage
disk_usage=$(df -h)

# Generate running processes
processes_info=$(ps aux --sort=-%mem | head -n 20)

# Write the report to the file
{
    echo "System Information Report"
    echo "========================"
    echo ""
    echo "System Uptime:"
    echo "$uptime_info"
    echo ""
    echo "Memory Usage:"
    echo "$memory_info"
    echo ""
    echo "CPU Load:"
    echo "$cpu_load"
    echo ""
    echo "Disk Usage:"
    echo "$disk_usage"
    echo ""
    echo "Running Processes (Top 20 by Memory Usage):"
    echo "$processes_info"
} > "$report_file"

echo "System information report has been saved to '$report_file'."
```

### How it works:
1. **Define Report File**: Sets the name of the file where the report will be saved.
2. **System Uptime**: Uses `uptime -p` to get the system's uptime in a human-readable format.
3. **Memory Usage**: Uses `free -h` to get memory usage in a human-readable format.
4. **CPU Load**: Uses `uptime` and `awk` to extract the CPU load averages.
5. **Disk Usage**: Uses `df -h` to get disk usage statistics in a human-readable format.
6. **Running Processes**: Uses `ps aux` to list running processes sorted by memory usage and selects the top 20.
7. **Write Report**: Outputs all collected information to the `system_report.txt` file with appropriate headings.

### Usage:
Save the script as `system_report.sh`, make it executable with `chmod +x system_report.sh`, and run it with:

```bash
./system_report.sh
```

This script will generate a system information report and save it to `system_report.txt`.
