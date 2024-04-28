[![CloudSploit](https://cloudsploit.com/img/logo-new-big-text-100.png "CloudSploit")](https://cloudsploit.com)

# GOOGLE / Logging / Audit Configuration Logging

## Quick Info

| | |
|-|-|
| **Plugin Title** | Audit Configuration Logging |
| **Cloud** | GOOGLE |
| **Category** | Logging |
| **Description** | Ensures that logging and log alerts exist for audit configuration changes. |
| **More Info** | Project Ownership is the highest level of privilege on a project, any changes in audit configuration should be heavily monitored to prevent unauthorized changes. |
| **GOOGLE Link** | https://cloud.google.com/logging/docs/logs-based-metrics/ |
| **Recommended Action** | Ensure that log alerts exist for audit configuration changes. |

## Detailed Remediation Steps
1. Log into the Google Cloud Platform Console.
2. Navigate to "Logbased metrics" under "Logging" (https://console.cloud.google.com/logs/metrics?walkthrough_id=panels--logging--query) and click on the "CREATE METRIC" button at the top.
3. On the "Metric editor" tab, enter the "Name" as "AuditConfig". For the required filter field, enter: **protoPayload.methodName="SetIamPolicy" AND protoPayload.serviceData.policyDelta.auditConfigDeltas:***
4. Click on the "Create metric" button at the bottom to create the logging metric.
5. On the "Logs-based metrics", under the "User-defined metrics" click on the 3 dots next to the newly created metric and click on the "create alert from metric."
6. On the "Create alert" page, select the "Aggregator" as per the requirement and select the "Configuration" from the dropdown menu accordingly.
8. Once the settings are "Saved", enter the name of the alarm.
9. Click on the "Save" button at the bottom to make the chanes.
