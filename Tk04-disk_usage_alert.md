## Task4>> Disk Usage Alert: Write a script that checks the disk usage of the root filesystem. If the disk usage is above 80%, the script should send an email alert to the system administrator.

### Bash script that checks the disk usage of the root filesystem and sends an email alert if the usage exceeds 80%. This script uses the `df` command to check disk usage and `mail` (or `mailx`) to send the email. You might need to install and configure an email utility if it’s not already set up on your system.

### Script:

```bash
#!/bin/bash

# Set email details
admin_email="bharatbhushan05@outlook.com"
subject="Disk Usage Alert: Root Filesystem"
message="Warning: Disk usage on the root filesystem has exceeded 80%."

# Check disk usage
disk_usage=$(df / | grep / | awk '{ print $5 }' | sed 's/%//')

# Define threshold
threshold=80

# Check if disk usage exceeds the threshold
if [ "$disk_usage" -ge "$threshold" ]; then
    # Send email alert
    echo "$message" | mail -s "$subject" "$admin_email"
fi
```

### How it works:
1. **Email Details**: Set `admin_email` to the email address of the system administrator.
2. **Check Disk Usage**: The `df /` command provides disk usage information for the root filesystem. The `grep /` filters the relevant line, `awk '{ print $5 }'` extracts the usage percentage, and `sed 's/%//'` removes the percentage sign.
3. **Threshold**: Defines the usage threshold (80% in this case).
4. **Check and Send Email**: Compares current disk usage with the threshold. If the usage is greater than or equal to the threshold, the script sends an email alert.

### Usage:
1. Save the script as `disk_usage_alert.sh`.
2. Make it executable with `chmod +x disk_usage_alert.sh`.
3. Run the script manually or set up a cron job to run it periodically (e.g., daily).

### Setting Up a Cron Job:
To automate the script to run daily, add the following line to your crontab (`crontab -e`):

```bash
0 2 * * * /path/to/disk_usage_alert.sh
```

This cron job runs the script daily at 2 AM. Adjust the path to where you saved the script.
