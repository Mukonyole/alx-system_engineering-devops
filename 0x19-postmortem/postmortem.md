Postmortem Report: System Outage on August 10, 2024
Incident Date: August 16, 2024
Incident Time: 10:00 AM - 12:30 PM (EAT)
Author: Evans Mukonyole, Senior DevOps Engineer
Date of Postmortem: August 16 , 2024

Incident Summary
On August 16, 2024, the production team experienced a complete outage lasting approximately 2 and half hours, from 10:00 AM to 12:30 PM (EAT). The outage was caused by a failure in the primary database server, which led to the unavailability of our web application. During this time, users were unable to access the service, resulting in significant customer impact.

Impact
Customer Impact: All users were unable to access the service during the outage.
Business Impact: Estimated revenue loss of $200,000 due to downtime and potential SLA breaches.
Reputational Impact: Several customers expressed concerns on social media, and three major clients requested formal explanations.

Timeline
Time (EAT)  
10:00 AM        Monitoring alerts triggered, indicating a drop in Database response.
10:05 AM        Engineers began investigating the issue.
10:15 AM        Identified that the primary Database server was unresponsive.
10:25 AM        Attempted to restart the Database server, but it failed to come back online.
10:40 AM        Decision made to failover to the standby Database server.
11:00 AM        Failover to standby completed, but issues persisted due to corrupted replication of data.
11:30 AM        Engineers identified and corrected the replication issue.
12:00 PM        System gradually began restoring services.
12:30 PM        All services fully restored, and monitoring returned to normal.

Root Cause
The primary cause of the outage was a failure in the database server due to an unexpected hardware fault. When attempting to failover to the standby server, replication data was found to be corrupted, which delayed the restoration of services.

Contributing Factors
Lack of Redundancy: The primary and standby database servers were located in the same physical data centre, making them vulnerable to shared risks.
Insufficient Monitoring: The monitoring system did not detect the initial corruption in the replication data, leading to delays in recovery.
Outdated Failover Procedures: The documented failover procedures were outdated, leading to confusion during the incident.
Lessons Learned
Improve Redundancy: Ensure that primary and standby systems are in separate physical locations or availability zones to prevent shared points of failure.
Enhance Monitoring: Implement more comprehensive monitoring to detect issues in replication data before a failover is needed.
Review and Update Procedures: Regularly review and update failover procedures to ensure they reflect the current environment and technologies.

Action Items
Deploy a second standby database server in a different data centre.
Enhance monitoring tools to include replication data integrity checks. 
Conduct a comprehensive review of all disaster recovery and failover procedures.
Conduct a team-wide training session on updated failover procedures.

Follow-Up
A follow-up meeting is scheduled for September 5,, 2024, to review the progress on action items and discuss any further improvements needed.

Conclusion
This incident highlighted several areas for improvement, particularly in redundancy and failover processes. By addressing the action items identified, we aim to prevent similar incidents in the future and improve our overall resilience.

