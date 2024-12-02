# Log Monitoring and Automation

## Objective


This Lab involves monitoring network logs for unusual activity, such as repeated failed login attempts, on the Linux system. The goal is to automate the log monitoring process, identify potential security threats (Indicators of Compromise or IoCs), and generate alerts when specific thresholds are exceeded. In this Lab we will create a Python script that routinely checks system logs for anomalies and outlines the process for providing weekly updates. The automation is implemented using Python and Bash scripts .

## Project Goals

- Enhance network security by identifying anomalies in system logs.
- Automate detection of failed login attempts and unusual network behavior.
- Lay the foundation for future improvements, including centralized log management.
  
### Skills Learned

- Hand on experience on Automation using Python and Bash Script.
- Proficiency in analyzing and interpreting network logs.
- Ability to generate and recognize attack signatures and patterns.
- Enhanced knowledge of network protocols and security vulnerabilities.
- Development of critical thinking and problem-solving skills in cybersecurity.

### Tools Used
- Python: For log parsing, anomaly detection, and generating reports.
- Bash Scripts: For scheduling automated log monitoring tasks.
- Linux: As the primary environment for script execution.
- Future Technologies: ELK stack and machine learning (planned).

## Steps
drag & drop screenshots here or use imgur and reference them using imgsrc

Every screenshot should have some text explaining what the screenshot is about.

Example below.

*Ref 1: Network Diagram*

## Workflow Structure

The following workflow is designed to efficiently monitor logs, report anomalies, and alert for unusual activities:
### Log Review
-	Schedule a CRON job to review server access logs every Friday, focusing on login activity.
- Implement an automated script to record and monitor unusual behavior, such as the number of login attempts from a specific IP address.
### Automation
-	Develop a Bash script on the Linux server to extract and filter Apache logs for failed login attempts using the cp and grep commands.
-	Use a Python script to format and display failed login attempts against a predefined threshold.
### Threshold Setup
-	Define a threshold where if a login attempt is made 5 times within a 30-minute window, the event will be recorded and flagged for further analysis.
### Saving Filtered Logs
-	Filter logs based on the threshold, save the results on the host machine for further review, and notify management if necessary.
-	Iterating for Changes in the Environment
-	Continuously monitor changes in the environment and make adjustments to improve efficiency and accuracy.

![image](https://github.com/user-attachments/assets/547abde3-9747-4295-ab32-b44fb44540b5)
### Explanation
In the script above we set up bash script to alert us if there were more than 5 login attempt in the test_apache_server.txt . After running failed_login_report.txt we found there was no activity detected and returned the output the time stamp for record keeping 

### Using Python and regular expression for Log analysis
Pyhon is used to simplify complex data and make it presentable for us to understand what is going on with logs (The Python Tutorial, n.d.). Using regular expression in python we matched IP Address with timestamp and status coded to make it easy for us to detect unusual behaviour. Below status code “200” means successful login where as “404” means failed login and needs further analysis.

![image](https://github.com/user-attachments/assets/9df85dab-391f-4a1c-b4b0-71dc7eada3bb)
![image](https://github.com/user-attachments/assets/9625bf86-e383-47d3-be7d-25769f4f4f1b)
#### Explanation
The expected out put will show the IP address with codes for failed login attempts and timestamp. status code “200” means successful login where as “404” means failed login and needs further analysis.
### Storing Log for Record-keeping and Documentation 
We can copy, move and filtered to access logging for safe keeping.
Below we have moved Apache logs to out host machine with date time stamp for security, analysis and reporting to manager. 

![image](https://github.com/user-attachments/assets/b2a059a6-9fec-437e-b158-bb6a01a6fcc8)

![image](https://github.com/user-attachments/assets/7ac48fac-d2e2-48c1-9e08-73782c519b2e)

#### Automating Log review for efficiency and Accuracy
Explanation:
We can automate log review Using CRON tab (Sharma & Sharma, 2023) and review then on a specific day of the week. Below is the code if we want to review it every Friday automatically.
0 12 * * 5: This schedules the script to run every Friday at 12:00 PM.
•	0: Minute (0th minute of the hour).
•	12: Hour (12 PM).
•	*: Any day of the month.
•	*: Any month.
•	5: The day of the week (5 represents Friday).
![image](https://github.com/user-attachments/assets/6c728027-e71e-4649-bcfa-dc3af0a289d0)
![image](https://github.com/user-attachments/assets/cab82df2-b851-4a6e-86ad-246e8f7b0115)

Expected Output (Log monitoring)
In the script we set up bash script to alert us if there were more than 5 login attempt in the test_apache_server.txt . After running failed_login_report.txt we found there was no activity detected and returned the output the time stamp for record keeping.
After running failed_login_reprot.txt we found there was no activity detected and returned the output the time stamp for record keeping. If there were more than 5 login attempts it would be recorded.

![image](https://github.com/user-attachments/assets/7974b738-1f76-4a1d-81ad-bfb7f95b8b48)
### Log Output using Pyhton 
The expected out put will show the IP address with codes for failed login attempts and timestamp. status code “200” means successful login where as “404” means failed login and needs further analysis.
![image](https://github.com/user-attachments/assets/e9c54e16-d243-4bad-88d7-c399435cc854)

### Expected Output when moving the log for to a differnet location
We can copy, move and filtered to access logging for safe keeping.
Below we have moved Apache logs to out host machine with date time stamp for security, analysis and reporting to manager. 
Below is the log when opened with text editor after moving it to the host machine.
![image](https://github.com/user-attachments/assets/f994d521-366e-4552-9d61-281be9843f68)

Expected Output for when using Automation using CRON Tab
Below is the output we would see on Friday. it is set up to show log every Friday of the week of every month continuously

![image](https://github.com/user-attachments/assets/1aa54fe9-63e0-4abe-b937-ab1627083bcd)


## Unusual Behaviour
We can define what we consider unusual behaviour by setting up threshold and creating necessary script.
For this report example of unusual behaviour are
-5 or more failed login attempts with a time interval of 30 minutes
- Single specific IP used to make failed login attempts
-	Website or Domain used for failed login attempts. 
-	Type of account used for login (for example root and administrator)
  
## Further Enhancement
- Automated Log Rotation and Archiving:  Use logrotate to manage log files effectively Automatically rotate, compress, and archive log files to manage disk space and keep logs organized. We can configure logrotate to periodically handle your Apache log files.
- Integrate with Log Management Tools:  Use tools like ELK Stack (Elasticsearch, Logstash, Kibana) for advanced log analysis.
- Use of Data Aggregation and Visualization: Aggregate log data and create visualizations using Python libraries like pandas and matplotlib.
