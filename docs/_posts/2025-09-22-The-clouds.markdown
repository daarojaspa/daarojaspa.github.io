---
title: "Getting the clouds"
category: Tools
--- 
The old way was: each company bought their own server. That server was never turned off, and if you needed a bigger one or had 
to move your headquarters—well, that was a big task.  

Then virtual machines became popular and evolved. If you had a lot of money, you could make a huge investment in buildings and 
servers, build virtual machines on those servers, and then rent those virtual machines.  

That’s how **cloud computing** was born. The cloud is just a bunch of servers you can use, but that aren’t yours.  

The average Joe normally just uses storage services like Google Drive, Google Photos, Netflix, Gmail, or Dropbox, with a cute 
interface and no need of knolege on how they work. But you can also use **computing services** (e.g., running your programs 
on someone else’s computer using the internet as a communication system).This is different from the 1950s, where you also used
 someone else’s computer (a mainframe) but had to be physically present to use it.

---

## Business Model

This business model allows small players to have access to top-of-the-line hardware at lower costs, in an easy-to-scale fashion.  

Now let’s talk about some acronyms:

- **IaaS**: You pay for the virtual machines but you are in charge of managing how you use them (OS, storage, networks).  
  Example: EC2 from AWS. Use it when you need to train big models or do heavy computing (training).  

- **PaaS**: The provider also handles OS, storage settings, and security patches.  
  It’s like hiring a catering service: they provide the kitchen, the cooking, and the ingredients, and you pick the menu (what to run in that environment).  
  Use it when you need to serve models as APIs quickly (deploying).  

- **SaaS**: You go out to a restaurant, the menu is set, and you pick what you want.  
  Example: You pay for a prebuilt monitoring service for an ML model that you run in a PaaS service and that was trained in an IaaS virtual machine.  

---

## AWS and Cloud Services

When you create a new AWS account for the first time, you will probably be overwhelmed because it’s a huge site with many options and panels, which change depending on some factors. It’s not very comprehensible really—I would say **WCAG 2.2** accessibility guidelines are not met.  

AWS has more than 200 services, and they are not the only cloud provider. So I asked GPT for an easy-to-map classification of the services. This makes it almost a 1-to-1 mapping with the other two big providers (GCP and Azure).

### Networking and Security
Connecting resources with safety precautions and managing users and permissions.  
Like you would on a PC or local network.

- **AWS**: VPC (networks), CloudFront (CDN), Route 53 (DNS), IAM (identity)  
- **Azure**: Virtual Network, Front Door/CDN, DNS, Active Directory  
- **GCP**: VPC, Cloud CDN, Cloud DNS, IAM  

### Compute
Where your code runs.

- **AWS**: EC2 (VMs), Lambda (serverless), ECS/EKS (containers, Kubernetes)  
- **Azure**: Virtual Machines, Azure Functions, AKS  
- **GCP**: Compute Engine, Cloud Functions, GKE  

### Storage
Any kind of data. Like a folder in your local PC, with a flat structure where you use keys or paths to upload/download.

- **AWS**: S3 (object storage), EBS (block storage), Glacier (archival)  
- **Azure**: Blob Storage, Disk Storage, Archive Storage  
- **GCP**: Cloud Storage, Persistent Disk, Nearline/Coldline  

### Databases and Analytics
Structured or semi-structured data built for efficiency in information access.  
Not flat like storage. If you’re a data analyst, this is your niche.

- **AWS**: RDS (SQL), DynamoDB (NoSQL), Redshift (data warehouse), Athena (querying)  
- **Azure**: SQL Database, Cosmos DB, Synapse Analytics  
- **GCP**: Cloud SQL, Firestore, BigQuery  

### AI & ML Development Tools
ML pipelines, AI services, and tools to manage applications.

- **AWS**: SageMaker (ML), Rekognition (vision), Comprehend (NLP), CodePipeline, CloudWatch  
- **Azure**: Azure ML, Cognitive Services, DevOps  
- **GCP**: Vertex AI, Vision/NLP APIs, Cloud Build, Cloud Monitoring  

---

## Regions

Regions represent the physical locations where the data centers are. Depending on the region and services, prices will change. This applies to all providers.  

When picking a region, you want to select the one that:  
- Has the services you need  
- Offers the best prices  
- Is near your clients  

### Global vs Regional Services
- **Global**: Networking and identity services (IAM, DNS, billing)  
- **Regional**: Most others. Some can be accessed globally by paying extra or combining them with networking services (so paying extra)  

The AWS console (web page) changes depending on which region you have selected.  

### Tips
- If you’re experimenting for the first time, pick **us-east-1** (widest availability).  
- Use the search bar (it doesn’t filter by region and is often faster).  
- Bookmark services you use frequently.  
- Learn the **AWS CLI** or SDK if UI changes mess with you a lot (e.g., if you use a screen reader).  

---

## Cheat Sheet for ML Engineers

Here’s a quick guide for ML engineers starting with cloud and not sure where to begin:

| **Category**                   | **AWS** (most known for ML beginners ⭐)                             | **Azure**              | **GCP**         |
| ------------------------------ | ------------------------------------------------------------------- | ---------------------- | --------------- |
| **Compute (Run code)**         | **Lambda** ⭐ (serverless, easy to deploy small models/APIs)         | Azure Functions        | Cloud Functions |
| **Storage (Save data/models)** | **S3** ⭐ (store datasets, models, logs)                             | Blob Storage           | Cloud Storage   |
| **Databases & Analytics**      | **RDS** ⭐ (managed SQL, great for ML feature storage)               | SQL Database           | Cloud SQL       |
| **Networking & Security**      | **IAM** ⭐ (manage roles/permissions, critical for safe deployments) | Azure Active Directory | IAM             |
| **AI/ML & Dev Tools**          | **SageMaker** ⭐ (train, deploy, monitor ML models)                  | Azure ML               | Vertex AI       |

I hope this broad schema has helped make your first encounter with a cloud platform more digestible. You are doing great, keep up the good work.
