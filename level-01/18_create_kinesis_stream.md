### Task

The Nautilus DevOps team needs to create an AWS Kinesis data stream for real-time data processing. This stream will be used to ingest and process large volumes of streaming data, which will then be consumed by various applications for analytics and real-time decision-making.

1. The stream should be named `datacenter-stream`.
2. Use `Terraform` to create this Kinesis stream.

### Solution

#### main.tf

```terraform
resource "aws_kinesis_stream" "nautilus" {
    name        = "datacenter-stream"
    shard_count = 1
}
```
