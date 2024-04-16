
# GOOGLE / Logging / Project Ownership Logging

## Quick Info

| | |
|-|-|
| **Plugin Title** | Project Ownership Logging |
| **Cloud** | GOOGLE |
| **Category** | Logging |
| **Description** | Ensures that logging and log alerts exist for project ownership assignments and changes |
| **More Info** | Project Ownership is the highest level of privilege on a project, any changes in project ownership should be heavily monitored to prevent unauthorized changes. |
| **GOOGLE Link** | https://cloud.google.com/logging/docs/logs-based-metrics/ |
| **Recommended Action** | Ensure that log alerts exist for project ownership assignments and changes. |

## Detailed Remediation Steps
1. Log in to the Google Cloud Platform Console.
2. Navigate to "Logbased metrics" under "Logging" (https://console.cloud.google.com/logs/metrics?walkthrough_id=panels--logging--query) and click on the "CREATE METRIC" button at the top.</br>  
3. On the "Metric editor" tab, enter the "Name" and "Description" </br> For the required filter field, enter: **(protoPayload.serviceName="cloudresourcemanager.googleapis.com") AND (ProjectOwnership OR projectOwnerInvitee) OR (protoPayload.serviceData.policyDelta.bindingDeltas.action="REMOVE" AND protoPayload.serviceData.policyDelta.bindingDeltas.role="roles/owner") OR (protoPayload.serviceData.policyDelta.bindingDeltas.action="ADD" AND protoPayload.serviceData.policyDelta.bindingDeltas.role="roles/owner")** </br> <img src="/resources/google/logging/project-ownership-logging/step7.png"/>
4. Click on the "Create metric" button at the bottom to make the changes.</br> <img src="/resources/google/logging/project-ownership-logging/step8.png"/>
5. On the "Logs-based metrics", under the "User-defined metrics" click on the 3 dots next to the newly created "Project Ownership Logging" metric and click on the "create alert from metric."</br> <img src="/resources/google/logging/project-ownership-logging/step9.png"/>
6. Make sure the "Monitoring Filter" is set to metric.type="logging.googleapis.com/user/ProjectOwnership"
7. Enter the "Condition, Threshold and Minute" of the above "Configuration" accordingly and click on the "Save" button to make the changes.</br> <img src="/resources/google/logging/project-ownership-logging/step11.png"/>
8. Once the settings are "Saved", enter the name of the alarm and select "Policy triggers" condition from the dropdown menu.</br> <img src="/resources/google/logging/project-ownership-logging/step12.png"/>
9. Click on the "Save" button at the bottom to make the changes.</br> <img src="/resources/google/logging/project-ownership-logging/step13.png"/>
10. Repeat steps for any GCP project where this is required.
