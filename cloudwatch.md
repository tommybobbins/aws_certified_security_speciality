# Cloudwatch

- EC2 metrics every 5 minutes (free).
- Detailed EC2 monitoring every 1 minute (chargeable).
- Unified CloudWatch Agent sends system-level metrics for EC2 and on-premise servers.
- System level metrics include memory and disk usage.
- Can publish custom matrics using CLI or API.
- Custom metrics are in Standard Resolution or High Resolution.

## Metric Alarm

Performs one or more actions based on a single metrics

## Composite Alarm

Uses a rule expression and takes into account multiple alarms
- OK - within a threshold.
- ALARM - outside a threshold.
- INSUFFICIENT_DATA - not enough data

## Cloudwatch Subscription Filter
Send to:
- Cloudwatch->Opensearch
- Cloudwatch->Lambda

## Cross-Account log data sharing

- Share Cloudwatch logs across accounts.
- Kinesis data streams is the only supported destination.
- Log data sender: Send log data to the recipient.
- Log data recipienct: Send data to a Kinesis Data Stream.

## Cloudwatch logs to S3

- Bucket cannot be encrypted with KMS, but can be encrypted with SSE.
- Bucket policy allowing logs.region to putobject.
- Configure the export from Cloudwatch logs.

## Cloudwatch Log aggregations

- Multi-account  - CW logs -> Subscription Filter-> Kinesis data stream-> Kinesis Data Firehose->S3
- Each account must have cross account subscription. Subscription Filter in Account 1, Subscription Destination in Account 2 (receiving account)-> Permission to write to Kinesis Data Streams via IAM role.