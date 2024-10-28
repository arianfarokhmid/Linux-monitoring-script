# System Monitoring Script

This script provides a comprehensive overview of system health, covering CPU, memory, disk, network traffic, top processes, and system logs. It can be run manually or automated with cron for continuous monitoring.

## Breakdown of the Script

1. **CPU Usage**  
   Uses `mpstat` to monitor CPU load, focusing on idle time. A low idle value suggests high CPU load.
   
2. **Memory Usage**  
   Uses `free -h` for a human-readable summary of memory and swap usage. High memory usage can indicate a resource-heavy application.
   
3. **Disk Usage**  
   Uses `df -h` to show disk space usage for each partition. Low disk space can cause performance degradation or system crashes.
   
4. **Network Traffic**  
   Uses `ifstat` to monitor incoming and outgoing network traffic on a specific interface (e.g., `eth0`).
   
5. **Top 5 Memory and CPU Consuming Processes**  
   Uses `ps` to list the top 5 processes consuming the most memory and CPU, helping to identify resource-intensive tasks.
   
6. **System Logs Monitoring**  
   Uses `journalctl` to display recent errors from system logs. This helps identify issues that may not yet impact performance but need investigation.

## Automating the Monitoring Script

While the script can be run manually, automation with `cron` makes it more powerful by running it at set intervals.

### Install Required Packages

```bash
sudo apt install sysstat ifstat
