# Serverless Service Alternatives Report

**Course:** ST8917 – Serverless Applications  
**Assignment:** 2 – Serverless Service Alternatives Report  
**Author:** Ajay Morla  
**Date:** August 15, 2025  

---

## 📌 Objective
This report compares **core Azure serverless services** used in the course with their closest equivalents in **Amazon Web Services (AWS)** and **Google Cloud Platform (GCP)**.  
The comparison covers:

- **Overview**
- **Core Features**
- **Triggers & Bindings**
- **Integration Options**
- **Monitoring & Observability**
- **Pricing**
- **Strengths & Weaknesses**

---

## 1. Azure Functions

**AWS Equivalent:** AWS Lambda  
**GCP Equivalent:** Cloud Functions  

| Criteria | Azure Functions | AWS Lambda | GCP Cloud Functions |
|----------|-----------------|------------|----------------------|
| **Overview** | Event-driven compute that runs code on demand. | Event-driven compute with multiple triggers. | Fully managed FaaS for event-driven workloads. |
| **Triggers & Bindings** | HTTP, Timer, Blob, Queue, Event Hub, Event Grid, Service Bus, Cosmos DB. | API Gateway, S3, DynamoDB, SNS, SQS, EventBridge. | HTTP, Pub/Sub, Storage, Firestore, Firebase. |
| **Integration** | Strong Azure service bindings + GitHub Actions & Azure DevOps. | Tight AWS integration; supports SAM & Serverless Framework. | Native GCP services + Cloud Build CI/CD. |
| **Monitoring** | Azure Monitor, App Insights, Log Analytics. | CloudWatch Logs, Metrics, X-Ray. | Cloud Logging, Cloud Monitoring. |
| **Pricing** | Pay-per-execution + GB-sec. | Pay-per-request + compute time. | Pay-per-invocation + GB-sec. |

**Analysis:**  
- Strength: Rich built-in bindings reduce boilerplate code.  
- Weakness: Cold start latency can be higher than AWS Lambda.

---

## 2. Durable Functions

**AWS Equivalent:** Step Functions  
**GCP Equivalent:** Workflows  

| Criteria | Azure Durable Functions | AWS Step Functions | GCP Workflows |
|----------|-------------------------|--------------------|---------------|
| **Overview** | State management & orchestration inside Functions. | Workflow orchestration with state machines. | Orchestration using YAML/JSON definitions. |
| **Patterns** | Chaining, fan-out/fan-in, async APIs, human approval. | Sequential, parallel, branching. | Sequential, parallel, error handling. |
| **Integration** | Works with Functions, Logic Apps, Event Grid, Service Bus. | Deep AWS service integrations. | Cloud Functions, Cloud Run, Pub/Sub. |
| **Monitoring** | App Insights + Durable Hub metrics. | CloudWatch, execution history. | Cloud Logging, Execution history. |
| **Pricing** | Per execution + storage for state. | Per state transition. | Per step execution. |

---

## 3. Azure Logic Apps

**AWS Equivalent:** Step Functions (Express) / AppFlow  
**GCP Equivalent:** Workflows + AppSheet  

| Criteria | Azure Logic Apps | AWS Step Functions Express / AppFlow | GCP Workflows + AppSheet |
|----------|------------------|---------------------------------------|--------------------------|
| **Overview** | Low-code workflow automation with 500+ connectors. | Express for lightweight orchestration; AppFlow for SaaS data flows. | Workflows for orchestration; AppSheet for no-code automation. |
| **Triggers** | Timer, HTTP, Event Grid, Service Bus, SaaS connectors. | API Gateway, EventBridge, service events. | HTTP, Pub/Sub, SaaS connectors via AppSheet. |
| **Integration** | Azure services + SaaS connectors. | AWS ecosystem + SaaS via AppFlow. | GCP services + SaaS connectors. |
| **Monitoring** | Azure Monitor, run history. | CloudWatch, X-Ray. | Cloud Logging, execution history. |
| **Pricing** | Per action/connector. | Per state transition/run. | Per step/user/month. |

---

## 4. Azure Service Bus (Queues & Topics)

**AWS Equivalent:** SQS (Queues) + SNS (Topics)  
**GCP Equivalent:** Pub/Sub  

| Criteria | Azure Service Bus | Amazon SQS + SNS | GCP Pub/Sub |
|----------|-------------------|------------------|-------------|
| **Overview** | Enterprise queues & topics. | Queues (SQS) and fan-out topics (SNS). | Global topic/subscription service. |
| **Features** | FIFO, dead-letter, duplicate detection. | FIFO & standard queues, message fan-out. | At-least-once delivery, push/pull. |
| **Integration** | Functions, Logic Apps, Event Grid. | Lambda, EventBridge. | Cloud Functions, Dataflow. |
| **Monitoring** | Azure Monitor. | CloudWatch. | Cloud Monitoring. |
| **Pricing** | Per op + size. | Per request + payload. | Per message + volume. |

---

## 5. Azure Event Grid

**AWS Equivalent:** EventBridge  
**GCP Equivalent:** Eventarc  

| Criteria | Azure Event Grid | AWS EventBridge | GCP Eventarc |
|----------|------------------|-----------------|--------------|
| **Overview** | Event routing at scale. | Event bus for AWS/SaaS/custom events. | Event routing from GCP/custom sources. |
| **Sources** | Azure services, custom topics, partners. | AWS services, SaaS partners. | GCP services, Pub/Sub, custom. |
| **Integration** | Functions, Logic Apps, Event Hubs. | Lambda, Step Functions. | Cloud Functions, Cloud Run. |
| **Monitoring** | Azure Monitor. | CloudWatch. | Cloud Logging. |
| **Pricing** | Per million ops. | Per event. | Per event. |

---

## 6. Azure Event Hubs

**AWS Equivalent:** Kinesis Data Streams  
**GCP Equivalent:** Pub/Sub (Streaming)  

| Criteria | Azure Event Hubs | AWS Kinesis | GCP Pub/Sub |
|----------|------------------|-------------|-------------|
| **Overview** | High-throughput event ingestion. | Real-time streaming ingest. | Global streaming messaging. |
| **Throughput** | Millions/sec, partitioned. | Shard-based scaling. | Auto-scaling, millions/sec. |
| **Integration** | Functions, Stream Analytics, Databricks. | Lambda, S3, Analytics. | Dataflow, BigQuery. |
| **Monitoring** | Azure Monitor. | CloudWatch. | Cloud Monitoring. |
| **Pricing** | Per throughput unit. | Per shard-hour + payload. | Per message + volume. |

---

## 7. Azure Blob Storage (Serverless Triggers)

**AWS Equivalent:** Amazon S3 + Event Notifications  
**GCP Equivalent:** Cloud Storage + Event Notifications  

| Criteria | Azure Blob Storage | Amazon S3 | GCP Cloud Storage |
|----------|--------------------|-----------|-------------------|
| **Overview** | Object storage with function triggers. | Object storage with event notifications. | Object storage with Pub/Sub notifications. |
| **Triggers** | Blob create/delete triggers Functions, Logic Apps. | S3 events to Lambda, SNS, SQS. | Notifications to Pub/Sub → Functions. |
| **Integration** | Functions, Event Grid, Durable Functions. | Lambda, Glue, Step Functions. | Cloud Functions, Dataflow. |
| **Monitoring** | Azure Monitor. | CloudWatch. | Cloud Monitoring. |
| **Pricing** | Per GB + transaction. | Per GB + request. | Per GB + request. |

---

## 8. Azure SQL Database (Serverless Tier)

**AWS Equivalent:** Amazon Aurora Serverless / RDS Serverless  
**GCP Equivalent:** Cloud SQL with autoscaling  

| Criteria | Azure SQL Database | Aurora Serverless | Cloud SQL (Serverless) |
|----------|--------------------|-------------------|------------------------|
| **Overview** | Managed relational DB, serverless compute option. | MySQL/Postgres serverless RDS variant. | Managed MySQL/Postgres with auto-scaling. |
| **Scaling** | Auto-pause/resume, per-second billing. | Auto-scaling ACUs. | Auto-scaling vCPU & RAM. |
| **Integration** | Functions, Logic Apps. | Lambda, Step Functions. | Cloud Functions, Workflows. |
| **Monitoring** | Azure Monitor, Query Insights. | CloudWatch. | Cloud Monitoring. |
| **Pricing** | Per compute-second + storage. | Per ACU-hour + storage. | Per vCPU/GB-hour. |

---

## 9. Azure Cognitive Services (Language API)

**AWS Equivalent:** Amazon Comprehend  
**GCP Equivalent:** Cloud Natural Language API  

| Criteria | Azure Cognitive Services | Amazon Comprehend | GCP NL API |
|----------|--------------------------|-------------------|------------|
| **Overview** | AI APIs for sentiment, key phrases, etc. | NLP service for sentiment, entities. | NLP service for syntax, sentiment, entities. |
| **Integration** | Logic Apps, Functions. | Lambda, Step Functions. | Cloud Functions, Workflows. |
| **Pricing** | Per 1,000 text records. | Per unit of text. | Per character/record. |

---

## 10. Microsoft Teams + Logic Apps (Webhook Automation)

**AWS Equivalent:** Amazon Chime SDK + EventBridge/Webhooks  
**GCP Equivalent:** Google Chat API + Workflows  

| Criteria | Azure Teams + Logic Apps | AWS Chime SDK + EventBridge | Google Chat API + Workflows |
|----------|--------------------------|-----------------------------|-----------------------------|
| **Overview** | Workflow automation triggered by Teams messages. | Event-driven messaging via Chime SDK + EventBridge. | Chat API triggers workflows. |
| **Integration** | Logic Apps, Functions, Cognitive Services. | Lambda, Step Functions. | Cloud Functions, AppSheet. |
| **Pricing** | Logic App run cost + Teams license. | Pay per event/message. | API usage + workflow steps. |

---

## 📊 Summary Table

| Azure Service | AWS Equivalent | GCP Equivalent |
|---------------|---------------|----------------|
| Azure Functions | AWS Lambda | Cloud Functions |
| Durable Functions | Step Functions | Workflows |
| Logic Apps | Step Functions Express / AppFlow | Workflows + AppSheet |
| Service Bus | SQS + SNS | Pub/Sub |
| Event Grid | EventBridge | Eventarc |
| Event Hubs | Kinesis Data Streams | Pub/Sub |
| Blob Storage | S3 | Cloud Storage |
| SQL Database (Serverless) | Aurora Serverless | Cloud SQL |
| Cognitive Services | Comprehend | NL API |
| Teams + Logic Apps | Chime SDK + EventBridge | Chat API + Workflows |

---

## 📝 Conclusion
Azure offers a **rich and tightly integrated serverless ecosystem** with bindings that simplify event-driven workflows. AWS excels in **global reach and service maturity**, while GCP stands out in **developer experience and data analytics integration**.  
Service choice should consider **ecosystem lock-in**, **latency**, **cost**, and **developer tooling**.

