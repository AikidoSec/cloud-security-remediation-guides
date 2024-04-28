
# GOOGLE / Logging / VPC Firewall Rule Logging

## Quick Info

| | |
|-|-|
| **Plugin Title** | VPC Firewall Rule Logging |
| **Cloud** | GOOGLE |
| **Category** | Logging |
| **Description** | Ensures that logging and log alerts exist for firewall rule changes |
| **More Info** | Project Ownership is the highest level of privilege on a project, any changes in firewall rule should be heavily monitored to prevent unauthorized changes. |
| **GOOGLE Link** | https://cloud.google.com/logging/docs/logs-based-metrics/ |
| **Recommended Action** | Ensure that log alerts exist for firewall rule changes. |

## Detailed Remediation Steps
1. Log in to the Google Cloud Platform Console.
2. Navigate to "Logbased metrics" under "Logging" (https://console.cloud.google.com/logs/metrics?walkthrough_id=panels--logging--query) and click on the "CREATE METRIC" button at the top.
3. On the "Metric editor" tab, enter the "Name" as "VPCFirewall". For the required filter field, enter: **(resource.type="gce_firewall_rule" AND protoPayload.methodName="v1.compute.firewalls.patch") OR (protoPayload.methodName="v1.compute.firewalls.insert")**
4. Click on the "Create metric" button at the bottom to create the logging metric.
5. On the "Logs-based metrics", under the "User-defined metrics" click on the 3 dots next to the newly created "VPC Firewall Rule Logging" metric and click on the "create alert from metric."</br> <img src="/resources/google/logging/vpc-firewall-rule-logging/step9.png"/>
6. On the "Create alert" page, select the "Aggregator" as per the requirement and select the "Configuration" from the dropdown menu accordingly.</br> <img src="/resources/google/logging/vpc-firewall-rule-logging/step10.png"/>
7. Enter the "Condition, Threshold and Minute" of the above "Configuration" accordingly and click on the "Save" button to make the changes.</br> <img src="/resources/google/logging/vpc-firewall-rule-logging/step11.png"/>
8. Once the settings are "Saved", enter the name of the alarm and select "Policy triggers" condition from the dropdown menu.</br> <img src="/resources/google/logging/vpc-firewall-rule-logging/step12.png"/>
9. Click on the "Save" button at the bottom to make the chanes.</br> <img src="/resources/google/logging/vpc-firewall-rule-logging/step13.png"/>

