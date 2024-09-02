!postmortem.jpg Image


Postmortem: Web Application Outage
Issue Summary
Duration: August 25, 2024, 14:00 GMT - August 25, 2024, 16:30 GMT (2 hours 30 minutes)

Impact: The web application was completely inaccessible to users. Approximately 85% of users experienced downtime, resulting in a significant drop in user activity and potential revenue loss.

Root Cause: A misconfiguration in the Nginx server settings caused a failure in the load balancer, leading to the web application being unreachable.

Timeline
14:00 GMT: Issue detected via monitoring alert indicating a sudden drop in traffic.
14:05 GMT: Initial investigation began by the on-call engineer.
14:15 GMT: Assumed the issue was related to a recent code deployment; rollback initiated.
14:30 GMT: Rollback completed, but the issue persisted.
14:45 GMT: Escalated to the DevOps team for further investigation.
15:00 GMT: DevOps team identified a misconfiguration in the Nginx server settings.
15:15 GMT: Misleading path: Investigated potential database connection issues.
15:30 GMT: Correct configuration applied to the Nginx server.
16:00 GMT: Web application started to recover.
16:30 GMT: Full service restored and confirmed stable.
Root Cause and Resolution
Root Cause: The root cause was a misconfiguration in the Nginx server settings. Specifically, the load balancer was not correctly distributing traffic to the backend servers due to an incorrect IP address configuration.

Resolution: The issue was resolved by correcting the Nginx configuration file to ensure the load balancer correctly routed traffic to the backend servers. The configuration was tested in a staging environment before being applied to production to ensure stability.

Corrective and Preventative Measures
Improvements:

Implement more rigorous testing of configuration changes in a staging environment before deploying to production.
Enhance monitoring to detect similar issues more quickly.
Tasks:

Patch Nginx Server: Update the Nginx configuration to include automated validation checks.
Add Monitoring: Implement additional monitoring on server memory and load balancer performance.
Review Deployment Process: Conduct a thorough review of the deployment process to identify and mitigate potential risks.
Training: Provide additional training for engineers on best practices for server configuration and deployment.
