
# GOOGLE / Logging / Storage Permissions Logging

## Quick Info

| | |
|-|-|
| **Plugin Title** | Storage Permissions Logging |
| **Cloud** | GOOGLE |
| **Category** | Logging |
| **Description** | Ensures that logging and log alerts exist for storage permission changes |
| **More Info** | Storage permissions include access to the buckets that store the logs, any changes in storage permissions should be heavily monitored to prevent unauthorized changes. |
| **GOOGLE Link** | https://cloud.google.com/logging/docs/logs-based-metrics/ |
| **Recommended Action** | Ensure that log alerts exist for storage permission changes. |

## Detailed Remediation Steps
1. Log into the Google Cloud Platform Console.
2. Navigate to "Logbased metrics" under "Logging" (https://console.cloud.google.com/logs/metrics?walkthrough_id=panels--logging--query) and click on the "CREATE METRIC" button at the top.
3. On the "Metric editor" tab, enter the "Name" as "StoragePermissionLogging". For the required filter field, enter: **resource.type=gcs_bucket AND protoPayload.methodName="storage.setIamPermissions"**
4. Click on the "Create metric" button at the bottom to create the logging metric.
5. On the "Logs-based metrics", under the "User-defined metrics" click on the 3 dots next to the newly created metric and click on the "create alert from metric."
6. On the "Create alert" page, select the "rolling-window function" to 'max' and select the "Configuration" from the dropdown menu accordingly.
8. Once the settings are "Saved", enter the name of the alarm.
9. Click on the "Save" button at the bottom to make the chanes.
