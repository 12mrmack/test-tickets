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

The implementation also includes reviewing **resource right-sizing opportunities** and evaluating **Spot Instances** before applying the cost allocation tags.

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

Review EC2 resources and identify underutilized instances before implementing cost allocation.

Check:

* Instance type
* CPU utilization
* Network utilization
* Current workload

<!-- Add screenshot here -->

<img src="screenshots/right-sizing-analysis.png" alt="Right-Sizing Analysis" />

---

### Step 2: Evaluate Spot Instances

Identify workloads that can tolerate instance interruption.

Suitable workloads may include:

* Jenkins workers
* CI/CD agents
* Batch processing
* Development/Test workloads

<!-- Add screenshot here -->

<img src="screenshots/spot-instance-analysis.png" alt="Spot Instance Analysis" />

---

### Step 3: Define Cost Allocation Tags

The following tags were defined for resource cost tracking:

| **Tag**      | **Example Value** |
| ------------ | ----------------- |
| Project      | OpenSearch        |
| Environment  | Production        |
| Owner        | DevOps            |
| CostCenter   | Engineering       |
| Application  | EmployeeAPI       |
| Rightsizing  | Review            |
| SpotEligible | Yes/No            |

---

### Step 4: Apply Tags to Resources

Apply the required tags to AWS resources using AWS Console or CLI.

Example:

```bash
aws ec2 create-tags \
  --resources <instance-id> \
  --tags \
    Key=Project,Value=OpenSearch \
    Key=Environment,Value=Production \
    Key=Owner,Value=DevOps \
    Key=CostCenter,Value=Engineering
```

<!-- Add screenshot here -->

<img src="screenshots/resource-tags.png" alt="Resource Tags" />

---

### Step 5: Activate Cost Allocation Tags

Navigate to:

```text
AWS Console
→ Billing and Cost Management
→ Cost Allocation Tags
→ User-defined cost allocation tags
```

Activate the required tags.

<!-- Add screenshot here -->

<img src="screenshots/cost-allocation-tags.png" alt="Cost Allocation Tags" />

---

### Step 6: Validate Tags

Verify that the tags are correctly attached to the resources.

```bash
aws ec2 describe-tags \
  --filters "Name=resource-id,Values=<instance-id>" \
  --output table
```

<!-- Add screenshot here -->

<img src="screenshots/tag-validation.png" alt="Tag Validation" />

---

### Step 7: Validate Cost Explorer

Open:

```text
AWS Console
→ Billing and Cost Management
→ Cost Explorer
```

Group the cost data by the activated Cost Allocation Tag.

<!-- Add screenshot here -->

<img src="screenshots/cost-explorer.png" alt="Cost Explorer Validation" />

---

# 4. Validation

| **Check**                | **Outcome**               |
| ------------------------ | ------------------------- |
| Right-sizing review      | Completed                 |
| Spot Instance evaluation | Completed                 |
| Resource tagging         | Tags applied successfully |
| Cost Allocation Tags     | Activated                 |
| Tag validation           | Verified                  |
| Cost Explorer            | Cost grouping validated   |

---

# 5. Result

AWS Cost Allocation Tags were implemented and validated successfully.

Resource right-sizing and Spot Instance opportunities were also reviewed as part of the AWS cost optimization process.

---

# 6. Contact Information

| **Name**     | **Email**                                                                                                                      |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| Maqbool Alam | [maqbul.alam.snaatak@mygurukulam.co](mailto:maqbul.alam.snaatak@mygurukulam.co)|

---

# 7. References

| **Topic**                                                                                                                     | **Description**                        |
| ----------------------------------------------------------------------------------------------------------------------------- | -------------------------------------- |
| [AWS Cost Allocation Tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-alloc-tags.html)                 | AWS Cost Allocation Tags documentation |
| [AWS Cost Explorer](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html)                             | AWS Cost Explorer documentation        |
| [AWS EC2 Spot Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-spot.html)                                 | AWS Spot Instance documentation        |
| [AWS EC2 Right-Sizing](https://docs.aws.amazon.com/whitepapers/latest/cost-optimization-reservation-models/right-sizing.html) | AWS right-sizing guidance              |
