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

Setting Up a Cron Job

To run the script every hour, follow these steps:

	1.	Open your crontab file:

crontab -e


	2.	Add the following line to schedule the script to run hourly:

0 * * * * /path/to/your_script.sh >> /var/log/system_monitor.log



This line will execute the script every hour on the hour, logging the output to /var/log/system_monitor.log.

Visualizing Your Data

While the script outputs data to the terminal or logs, visualizing it can be beneficial, especially for production environments. Tools like Grafana and Prometheus can collect and graph the data, providing interactive and visual representations of system performance over time.

Enhancing Security with Monitoring

Monitoring isn’t only about performance; it’s also critical for security. Examples:

	•	Log Monitoring: Watching system logs helps detect suspicious activities, like repeated login attempts or unauthorized access.
	•	Process Monitoring: Monitoring processes can reveal malware or unnecessary background tasks.
	•	Network Traffic: Tracking network traffic patterns can uncover potential security breaches.

Benefits of This Approach

Using a single script to monitor all key areas of your Linux system saves time and centralizes the monitoring process. This script provides a quick overview of system health at any time, and when combined with cron jobs and data visualization, it helps ensure smooth operations and early issue detection.

Helpful Tip: Customize this script to suit your system’s unique needs. You could add checks for hardware temperature, I/O statistics, or other metrics important to your environment.

