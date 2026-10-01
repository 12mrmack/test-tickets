# GoLang CI Checks Unit Testing Documentation

<img src="https://img.shields.io/badge/Application%20CI-Design-green?style=for-the-badge" />
<img src="https://img.shields.io/badge/GoLang-CI%20Checks-orange?style=for-the-badge" />
<img src="https://img.shields.io/badge/Unit%20Testing-blue?style=for-the-badge" />

---

# Author Table

| **Author**    | **Created On** | **Version** | **Last Updated By** | **Last Edited On** | **L0 Reviewer** | **L1 Reviewer** | **L2 Reviewer** |
| ------------- | -------------- | ----------- | ------------------- | ------------------ | --------------- | --------------- | --------------- |
| Maqbool Alam | 23-09-2026   | 1.0   | Maqbool Alam      | 23-09-2026    | Rajnish/Asma   | Pritam/Komal   | Abhishek/Manish Nautiyal  |

---

# Table of Contents

1. [Introduction](#1-introduction)
2. [What is Unit Testing](#2-what-is-unit-testing)
3. [Why Unit Testing is Required](#3-why-unit-testing-is-required)
4. [GoLang Unit Testing Workflow](#4-golang-unit-testing-workflow)

   * [4.1 Workflow Diagram](#41-workflow-diagram)
5. [Different Tools for Unit Testing](#5-different-tools-for-unit-testing)
6. [Tool Comparison](#6-tool-comparison)
7. [Advantages and Disadvantages](#7-advantages-and-disadvantages)
8. [Best Practices](#8-best-practices)
9. [Recommendation / Conclusion](#9-recommendation--conclusion)
10. [Proof of Concept (POC)](#10-proof-of-concept-poc)
11. [Contact Information](#11-contact-information)
12. [References](#12-references)

---

# 1. Introduction

Unit Testing is a CI check used to verify individual functions, methods, and components of a Go application.

It automatically validates application logic whenever new code is submitted to the repository.

---

# 2. What is Unit Testing

Unit Testing checks a small and independent part of an application to verify that it produces the expected result.

Go provides a built-in testing package that can be used to create and execute unit tests.

Example:

```text
Input → Function → Expected Output
  5   →  Add()   →      10
```

If the actual output does not match the expected output, the test fails.

---

# 3. Why Unit Testing is Required

Unit Testing is required in CI to verify that code changes do not break existing functionality.

It helps to:

* Detect bugs early.
* Validate application logic.
* Prevent regression issues.
* Improve code reliability.
* Automatically validate code changes.
* Stop failed tests from moving to later CI stages.

---

# 4. GoLang Unit Testing Workflow

The CI pipeline checks out the Go source code, downloads dependencies, runs unit tests, and validates the test result.

If the tests pass, the pipeline continues. If tests fail, the pipeline stops and requires the issue to be fixed.

## 4.1 Workflow Diagram

<details>
<summary>Click to Expand GoLang Unit Testing Workflow Diagram</summary>

<img width="445" height="611" alt="image" src="https://github.com/user-attachments/assets/37be76f8-5c32-438b-b52d-8f7b3d2f7845" />


</details>

---

# 5. Different Tools for Unit Testing

| **Tool**       | **Description**                                              |
| -------------- | ------------------------------------------------------------ |
| **Go testing** | Built-in Go package for writing and running unit tests.      |
| **Testify**    | Provides assertions, mocks, and test-suite utilities for Go. |
| **GoMock**     | Framework for creating mock objects for Go tests.            |
| **Ginkgo**     | Behaviour-driven development testing framework for Go.       |

---

# 6. Tool Comparison

| **Tool**       | **Main Purpose**     | **Ease of Use** | **CI Integration** | **Best Use Case**               |
| -------------- | -------------------- | --------------- | ------------------ | ------------------------------- |
| **Go testing** | Unit Testing         | Easy            | Excellent          | Standard Go projects            |
| **Testify**    | Assertions & Mocking | Easy            | Excellent          | Simple and readable tests       |
| **GoMock**     | Mocking              | Moderate        | Excellent          | Testing interfaces/dependencies |
| **Ginkgo**     | BDD Testing          | Moderate        | Excellent          | Behaviour-driven tests          |

---

# 7. Advantages and Disadvantages

| **Advantages**           | **Disadvantages**                                |
| ------------------------ | ------------------------------------------------ |
| Finds bugs early         | Tests require development effort                 |
| Built into Go            | Complex tests may require additional frameworks  |
| Easy CI integration      | Tests need maintenance                           |
| Helps prevent regression | Large test suites can increase CI execution time |

---

# 8. Best Practices

| **Best Practice**          | **Description**                                         |
| -------------------------- | ------------------------------------------------------- |
| Run Tests in CI            | Execute unit tests automatically for code changes.      |
| Use Table-Driven Tests     | Test multiple input/output combinations efficiently.    |
| Keep Tests Independent     | Avoid dependencies between individual tests.            |
| Mock External Dependencies | Use mocks when testing services or external components. |
| Check Test Coverage        | Use Go coverage tools to identify untested code.        |

---

# 9. Recommendation / Conclusion

Unit Testing should be included as a standard Go CI check to validate application logic before the code moves to later CI stages.

For the **POC, Go's built-in `testing` package will be used** because it is included with Go, requires no additional testing framework, and integrates directly with the standard Go toolchain.

**Selected Tool for POC: Go testing**

Testify or GoMock can be added when advanced assertions or dependency mocking is required.

---

# 10. Proof of Concept (POC)

A separate Proof of Concept has been created to demonstrate **GoLang Unit Testing in the CI pipeline**.

The POC demonstrates:

* Creating Go unit tests.
* Running tests using `go test`.
* Generating test results and coverage.
* Passing or failing the CI pipeline based on test results.

[Click here to view the GoLang Unit Testing POC](POC_URL)

**Running test on api location**
><img width="1081" height="792" alt="image" src="https://github.com/user-attachments/assets/8f12e689-b2e8-42a0-b54a-01b199e34e0a" />
><img width="1081" height="792" alt="image" src="https://github.com/user-attachments/assets/dc7404ed-1738-43d3-820d-2b6dddc7d852" />

**Run test on all directory**
><img width="1081" height="792" alt="image" src="https://github.com/user-attachments/assets/a458940b-cf23-4337-91b1-30d2df603f82" />
><img width="1081" height="792" alt="image" src="https://github.com/user-attachments/assets/ebd05eae-f744-406d-aaec-17f1417848eb" />

**Coverage Test**
><img width="1081" height="787" alt="image" src="https://github.com/user-attachments/assets/1f113ec9-fe03-4b86-b7e9-6cb7308e6b02" />
><img width="1081" height="787" alt="image" src="https://github.com/user-attachments/assets/4063fcbf-5961-4cc6-b4ca-f0639424fab4" />

**Reason why Unit Ttest fail**
><img width="1494" height="287" alt="image" src="https://github.com/user-attachments/assets/833067d9-8566-416d-9466-21b98d07103c" />


**Applicaion is running**
><img width="1081" height="148" alt="image" src="https://github.com/user-attachments/assets/6a8095f9-8654-4e29-9e2f-b47e43d4479f" />

**Frontend getting data from Employee-api means scylla running**
><img width="1081" height="787" alt="image" src="https://github.com/user-attachments/assets/a08b64ba-f6fc-4529-aa00-2e005486ccd8" />

---

# 11. Contact Information

| **Name** | **Email**                 |
| -------- | ------------------------- |
| Maqbool Alam  | [<maqbul.alam.snaatak@mygurukulam.co>](mailto:<maqbul.alam.snaatak@mygurukulam.co>) |

---

# 12. References

| **Topic**                                         | **Description**                                |
| ------------------------------------------------- | ---------------------------------------------- |
| [Go Testing Package](https://pkg.go.dev/testing)  | Official Go testing package documentation.     |
| [Go Test](https://go.dev/doc/tutorial/add-a-test) | Official Go guide for writing tests.           |
| [Testify](https://github.com/stretchr/testify)    | Official Testify repository and documentation. |
| [GoMock](https://github.com/uber-go/mock)         | Go mocking framework documentation.            |
| [Ginkgo](https://onsi.github.io/ginkgo/)          | Official Ginkgo documentation.                 |
