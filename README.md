# Serverless Service Alternatives Report

**Course:** ST8917 – Serverless Applications  
**Assignment:** 2 – Serverless Service Alternatives Report  
**Author:** Ajay Morla  
**Date:** August 15, 2025  

---

## 📌 Objective
This report compares six core Azure serverless services used in the course with their closest equivalents in Amazon Web Services (AWS) and Google Cloud Platform (GCP).  
The comparison covers **features, triggers/bindings, integration options, monitoring, pricing**, and **strengths/weaknesses** from a serverless architecture perspective.

---

## 1. Azure Functions

**AWS Equivalent:** AWS Lambda  
**GCP Equivalent:** Cloud Functions  

| Criteria | Azure Functions | AWS Lambda | GCP Cloud Functions |
|----------|-----------------|------------|----------------------|
| **Overview** | Event-driven compute service that runs code on demand with triggers/bindings. | Event-driven compute service that runs code in response to triggers. | Fully managed event-driven function execution service. |
| **Triggers & Bindings** | HTTP, Timer, Blob, Queue, Event Hub, Event Grid, Service Bus, Cosmos DB (input/output bindings). | API Gateway, S3, DynamoDB, SNS, SQS, EventBridge, CloudWatch Events. | HTTP, Cloud Pub/Sub, Cloud Storage, Firestore, Firebase events. |
| **Integration** | Deep integration with Azure services and CI/CD via GitHub Actions, Azure DevOps. | Tight AWS ecosystem integration; supports SAM & Serverless Framework. | Native GCP service integration; supports Cloud Build for CI/CD. |
| **Monitoring** | Azure Monitor, Application Insights, Log Analytics. | CloudWatch Logs & Metrics, X-Ray for tracing. | Cloud Logging, Cloud Monitoring, Error Reporting. |
| **Pricing** | Consumption-based: per execution + GB-sec memory usage. | Pay per request + compute time (ms) + memory allocation. | Pay per invocation + GB-sec compute usage. |

**Analysis:**  
- **Strengths:** Rich bindings in Azure Functions simplify integrations; good development tooling in VS Code.  
- **Weaknesses:** Cold start latency can be higher than AWS Lambda; fewer global regions.  

---

## 2. Durable Functions

**AWS Equivalent:** Step Functions  
**GCP Equivalent:** Workflows  

| Criteria | Azure Durable Functions | AWS Step Functions | GCP Workflows |
|----------|-------------------------|--------------------|---------------|
| **Overview** | Extension of Azure Functions for stateful workflows with chaining, fan-out/fan-in, and async orchestration. | Managed workflow service to coordinate AWS services using state machines. | Orchestrates services/functions into workflows using YAML/JSON syntax. |
| **Workflow Patterns** | Function chaining, fan-out/fan-in, async HTTP APIs, human interaction patterns. | Sequential, parallel, branching, error handling. | Sequential, parallel, error handling; HTTP call orchestration. |
| **Integration** | Azure Functions, Logic Apps, Event Grid, Service Bus. | Direct integration with AWS Lambda, SNS, SQS, DynamoDB, ECS, etc. | Calls to Cloud Functions, Cloud Run, Pub/Sub, external APIs. |
| **Monitoring** | Application Insights + Durable Task Hub metrics. | CloudWatch metrics, execution history, X-Ray. | Cloud Logging, Execution history in GCP console. |
| **Pricing** | Per execution + storage & I/O for orchestration state. | Per state transition. | Per step execution + call duration. |

**Analysis:**  
- **Strengths:** Durable Functions code-first approach fits developers already using Functions.  
- **Weaknesses:** Less visual than Step Functions; fewer built-in connectors than Logic Apps.  

---

## 3. Azure Logic Apps

**AWS Equivalent:** AWS Step Functions (Express) / AWS AppFlow  
**GCP Equivalent:** Workflows + AppSheet  

| Criteria | Azure Logic Apps | AWS Step Functions (Express) / AppFlow | GCP Workflows + AppSheet |
|----------|------------------|-----------------------------------------|--------------------------|
| **Overview** | Low-code workflow automation with 500+ connectors. | Step Functions Express for workflow orchestration; AppFlow for SaaS data integration. | Workflows for orchestration, AppSheet for no-code automation. |
| **Triggers** | Timer, HTTP, Event Grid, Service Bus, SaaS connectors (e.g., Salesforce, Office 365). | API Gateway, EventBridge, direct AWS service events. | HTTP, Pub/Sub, scheduler, SaaS connectors via AppSheet. |
| **Integration** | Deep integration with Azure + SaaS apps. | AWS ecosystem + some SaaS via AppFlow. | GCP services + SaaS connectors via AppSheet. |
| **Monitoring** | Azure Monitor, Run history view. | CloudWatch, X-Ray. | Cloud Logging, Execution history. |
| **Pricing** | Per action/connector execution. | Step Functions: per state transition; AppFlow: per flow run. | Per workflow step execution; AppSheet: per active user/month. |

**Analysis:**  
- **Strengths:** Rich SaaS connector library in Logic Apps.  
- **Weaknesses:** Can be more expensive at scale compared to function-based workflows.  

---

## 4. Azure Service Bus (Queues & Topics)

**AWS Equivalent:** Amazon SQS (Queues) + SNS (Topics)  
**GCP Equivalent:** Pub/Sub  

| Criteria | Azure Service Bus | Amazon SQS + SNS | GCP Pub/Sub |
|----------|-------------------|------------------|-------------|
| **Overview** | Enterprise messaging service with queues (point-to-point) and topics (pub/sub). | SQS for queues; SNS for pub/sub topics. | Global message ingestion and delivery in pub/sub model. |
| **Features** | FIFO queues, dead-letter queues, sessions, duplicate detection. | SQS: Standard & FIFO queues; SNS: message fan-out. | At-least-once delivery, topic-based publish/subscribe. |
| **Integration** | Azure Functions, Logic Apps, Event Grid. | Lambda triggers, integration with most AWS services. | Cloud Functions, Dataflow, BigQuery, Cloud Run. |
| **Monitoring** | Azure Monitor, Service Bus metrics. | CloudWatch metrics/logs. | Cloud Monitoring, Cloud Logging. |
| **Pricing** | Per operation + message size; tiers for Standard/Premium. | SQS/SNS: per request + payload size. | Per message + data volume. |

**Analysis:**  
- **Strengths:** Rich enterprise messaging features in Service Bus.  
- **Weaknesses:** Premium tier needed for low-latency, which increases cost.  

---

## 5. Azure Event Grid

**AWS Equivalent:** EventBridge  
**GCP Equivalent:** Eventarc  

| Criteria | Azure Event Grid | AWS EventBridge | GCP Eventarc |
|----------|------------------|-----------------|--------------|
| **Overview** | Event routing service for reactive programming at scale. | Event bus service for routing events from AWS services & SaaS apps. | Event routing from GCP services, SaaS, and custom sources. |
| **Event Sources** | Azure services, custom topics, partner events. | AWS services, SaaS partners, custom events. | GCP services, Pub/Sub topics, custom events. |
| **Integration** | Azure Functions, Logic Apps, Event Hubs, Service Bus. | Lambda, Step Functions, SNS, SQS. | Cloud Functions, Cloud Run, Workflows. |
| **Monitoring** | Azure Monitor, metrics, diagnostics. | CloudWatch metrics/logs. | Cloud Logging, metrics. |
| **Pricing** | Per million operations. | Per event published/consumed. | Per event delivered. |

**Analysis:**  
- **Strengths:** Native Azure integration; low-latency event routing.  
- **Weaknesses:** Smaller partner event ecosystem compared to EventBridge.  

---

## 6. Azure Event Hubs

**AWS Equivalent:** Kinesis Data Streams  
**GCP Equivalent:** Pub/Sub (Streaming)  

| Criteria | Azure Event Hubs | AWS Kinesis Data Streams | GCP Pub/Sub |
|----------|------------------|--------------------------|-------------|
| **Overview** | Big data event ingestion service for high-throughput streaming. | Real-time data streaming service for ingesting large-scale data. | Global messaging service supporting streaming workloads. |
| **Throughput** | Millions of events/sec; partitions for scale. | Shard-based scaling; thousands of records/sec per shard. | Automatic scaling; millions of messages/sec. |
| **Integration** | Azure Functions, Stream Analytics, Databricks, Synapse. | Lambda, Kinesis Data Analytics, S3, Redshift. | Dataflow, BigQuery, Cloud Functions, Cloud Run. |
| **Monitoring** | Azure Monitor, metrics, diagnostic logs. | CloudWatch metrics/logs. | Cloud Monitoring, Logging. |
| **Pricing** | Per throughput unit + data retention. | Per shard-hour + PUT payload units. | Per message + data volume. |

**Analysis:**  
- **Strengths:** Tight integration with Azure analytics stack.  
- **Weaknesses:** Throughput units pricing model can be less flexible than pay-per-use.  

---

## 7. Summary Comparison Table

| Azure Service | AWS Equivalent | GCP Equivalent |
|---------------|---------------|----------------|
| Azure Functions | AWS Lambda | Cloud Functions |
| Durable Functions | Step Functions | Workflows |
| Logic Apps | Step Functions (Express) / AppFlow | Workflows + AppSheet |
| Service Bus | SQS + SNS | Pub/Sub |
| Event Grid | EventBridge | Eventarc |
| Event Hubs | Kinesis Data Streams | Pub/Sub |

---

## 📊 Conclusion
Azure provides a **comprehensive serverless ecosystem** with strong integration and developer tooling, while AWS offers the **broadest global reach** and mature event-driven services, and GCP excels in **developer-friendly workflows** and **data analytics integration**.  
Choosing between them depends on factors like **ecosystem lock-in, latency requirements, global availability, and cost structure**.

