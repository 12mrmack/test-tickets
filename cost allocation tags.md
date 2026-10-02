# AWS Cost Allocation Tags

<img src="https://img.shields.io/badge/AWS-Cost%20Allocation%20Tags-orange?style=for-the-badge" />

---

# Author Table

| **Author**   | **Created On** | **Version** | **Last Updated By** | **Last Edited On** | **L0 Reviewer** | **L1 Reviewer** | **L2 Reviewer**          |
| ------------ | -------------- | ----------- | ------------------- | ------------------ | --------------- | --------------- | ------------------------ |
| Maqbool Alam | 30-09-2026     | 1.0         | Maqbool Alam        | 30-09-2026         | Rajnish/Asma    | Pritam/Komal    | Abhishek/Manish Nautiyal |

---

# Table of Contents

1. [Objective](#1-objective)
2. [Prerequisites](#2-prerequisites)
3. [Implementation Steps](#3-implementation-steps)
4. [Validation](#4-validation)
5. [Result](#5-result)
6. [Contact Information](#6-contact-information)
7. [References](#7-references)

---

# 1. Objective

Implement AWS Cost Allocation Tags to track and categorize AWS resource costs.

---

# 2. Prerequisites

| **Requirement**    | **Details**                                 |
| ------------------ | ------------------------------------------- |
| AWS Account        | Required for accessing AWS resources        |
| AWS Console Access | Billing and resource management permissions |
| EC2 Resources      | Resources to review and tag                 |
| Cost Explorer      | Required for cost validation                |

---

# 3. Implementation Steps

### Step 1: Review Resource Right-Sizing

Check:

* Instance type
* CPU utilization
* Network utilization
* Current workload

In our case we took 
Instance type = **c7i-flex.large**
Memory = 4GB
vCPU = 2

><img width="1456" height="772" alt="image" src="https://github.com/user-attachments/assets/41c273e0-0741-47c8-ace2-6b45a86df640" />

**5 Mintnues Spike**
/
><img width="1601" height="427" alt="image" src="https://github.com/user-attachments/assets/146a72af-89ed-4cb3-80c7-04177df2f15e" />
/
**1 Hours Spike**
><img width="1601" height="427" alt="image" src="https://github.com/user-attachments/assets/4a69c9ad-633d-4e43-9101-0374a75518b0" />

So according to Spike , we can take action accordingly

---

### Step 2: Spot Instances

Identify workloads that can tolerate instance interruption.

Suitable workloads may include:

* Jenkins workers
* CI/CD agents
* Batch processing
* Development/Test workloads

**Request for Spot Instance**
><img width="1720" height="659" alt="image" src="https://github.com/user-attachments/assets/9c269084-12c8-4345-a979-32df69db1124" />

**We Got Spot Instance**
><img width="1850" height="669" alt="image" src="https://github.com/user-attachments/assets/341e4ef4-a264-4013-aeb2-61e7f53e3553" />



---

### Step 3: Define Cost Allocation Tags

The following tags were defined for resource cost tracking:

| **Tag**      | **Example Value** |
| ------------ | ----------------- |
| Project      | OTMS              |
| Environment  | Production        |
| Owner        | DevOps            |
| CostCenter   | Finance       |

---

### Step 4: Apply Tags to Resources

Apply the required tags to AWS resources using AWS Console or CLI.

><img width="763" height="389" alt="image" src="https://github.com/user-attachments/assets/f5ee089c-9776-41c4-bec8-2adfacf4735b" />

---

### Step 5: Activate Cost Allocation Tags

><img width="951" height="495" alt="image" src="https://github.com/user-attachments/assets/734a055e-e776-4028-bb34-3e8981538292" />


---

### Step 6: Validate Cost Explorer

Open:

```text
AWS Console
→ Billing and Cost Management
→ Cost Explorer
```

Group the cost data by the activated Cost Allocation Tag.

><img width="1849" height="884" alt="image" src="https://github.com/user-attachments/assets/6706088b-d60a-4ca2-8cbc-529c3f0157ff" />

**Only Ec2 Service based Data found , But Tag based we haven't see any cost data because (No enough historical data to forecast your spend)**
><img width="1849" height="884" alt="image" src="https://github.com/user-attachments/assets/316b8c0f-d788-4222-a656-863b77689732" />


---

# 4. Validation

| **Check**                | **Outcome**               |
| ------------------------ | ------------------------- |
| Right-sizing review      | Completed                 |
| Spot Instance evaluation | Completed                 |
| Resource tagging         | Tags applied successfully |
| Cost Allocation Tags     | Activated                 |
| Cost Explorer            | Cost grouping validated   |

---

# 5. Result

AWS Cost Allocation Tags were implemented and validated successfully.

---

# 6. Contact Information

| **Name**     | **Email**                                                                                                                      |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| Maqbool Alam | [[maqbul.alam.snaatak@mygurukulam.co](mailto:maqbul.alam.snaatak@mygurukulam.co)](mailto:<maqbul.alam.snaatak@mygurukulam.co>) |

---

# 7. References

| **Topic**                                                                                                                     | **Description**                        |
| ----------------------------------------------------------------------------------------------------------------------------- | -------------------------------------- |
| [AWS Cost Allocation Tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-alloc-tags.html)                 | AWS Cost Allocation Tags documentation |
| [AWS Cost Explorer](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html)                             | AWS Cost Explorer documentation        |
| [AWS EC2 Spot Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-spot.html)                                 | AWS Spot Instance documentation        |
| [AWS EC2 Right-Sizing](https://docs.aws.amazon.com/whitepapers/latest/cost-optimization-reservation-models/right-sizing.html) | AWS right-sizing guidance              |
