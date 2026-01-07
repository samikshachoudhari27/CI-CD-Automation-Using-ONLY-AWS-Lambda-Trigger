# 🚀 CI/CD Automation Using ONLY AWS Lambda Trigger

## 📌 Project Overview

This project demonstrates a **fully serverless CI/CD automation pipeline built using only AWS Lambda triggers**, without using traditional CI/CD tools like **Jenkins, GitHub Actions, CodePipeline, or CodeBuild**.

The entire pipeline—from **code upload → build → test → deployment → notification**—is automated using **AWS Lambda and native AWS services**, making it **cost-effective, scalable, and Free-Tier friendly**.

This project is ideal for:

* Freshers learning **AWS DevOps**
* Serverless CI/CD architecture understanding
* Interview & resume-worthy DevOps projects

---

## 🏗️ Architecture Overview

**Core Idea:**

> Every CI/CD stage is triggered by **AWS Lambda**, not external CI/CD tools.

### 🔄 CI/CD Flow

1. **Developer uploads code** to S3
2. **S3 Event Trigger** invokes Lambda (Build Stage)
3. **Build Lambda** runs build logic (syntax check / package)
4. **Test Lambda** validates application
5. **Deploy Lambda** deploys code to EC2 / Lambda / S3
6. **CloudWatch Logs** capture execution logs
7. **SNS Notification** sends success/failure alerts

---

## 🎯 Features

* ✅ No Jenkins / No GitHub Actions
* ✅ 100% Serverless CI/CD
* ✅ Event-driven architecture
* ✅ AWS Free Tier compatible
* ✅ Modular Lambda functions
* ✅ Real-time logging with CloudWatch
* ✅ Email alerts using SNS

---

## 🧰 AWS Services Used

| Service             | Purpose               |
| ------------------- | --------------------- |
| AWS Lambda          | CI/CD logic execution |
| Amazon S3           | Source code storage   |
| Amazon CloudWatch   | Logs & monitoring     |
| Amazon SNS          | Notifications         |
| IAM                 | Secure permissions    |
| Amazon EC2 / Lambda | Deployment target     |

---

## 🛠️ Project Structure

```bash
lambda-cicd-automation/
│
├── build_lambda/
│   └── build.py
│
├── test_lambda/
│   └── test.py
│
├── deploy_lambda/
│   └── deploy.py
│
├── sample_app/
│   └── app.py
│
├── architecture/
│   └── cicd-architecture.png
│
└── README.md
```

---

## 🔧 Step-by-Step Implementation

### STEP 1️⃣: Create S3 Bucket

```bash
aws s3 mb s3://lambda-cicd-source-bucket
```

Upload application code to this bucket.

---

### STEP 2️⃣: Create IAM Role for Lambda

Permissions required:

* AmazonS3FullAccess
* CloudWatchLogsFullAccess
* AmazonSNSFullAccess

---

### STEP 3️⃣: Build Lambda Function

Triggered by **S3 PUT event**

**Responsibilities:**

* Validate source code
* Package artifacts
* Trigger Test Lambda

---

### STEP 4️⃣: Test Lambda Function

**Responsibilities:**

* Run unit tests
* Validate application
* If success → trigger Deploy Lambda

---

### STEP 5️⃣: Deploy Lambda Function

**Responsibilities:**

* Deploy app to:

  * EC2 OR
  * Lambda OR
  * S3 static hosting

---

### STEP 6️⃣: CloudWatch Logging

Monitor logs:

```bash
/aws/lambda/Lambda-CICD-Build
/aws/lambda/Lambda-CICD-Test
/aws/lambda/Lambda-CICD-Deploy
```

---

### STEP 7️⃣: SNS Notifications

Receive email alerts:

* ✅ Build Success
* ❌ Build Failure
* 🚀 Deployment Complete

---

## 🧪 Sample Lambda Code (Build Stage)

```python
def lambda_handler(event, context):
    print("Build started...")
    print("Code validated successfully")
    return {
        "statusCode": 200,
        "message": "Build completed"
    }
```

---

## 📊 Monitoring & Logs

* CloudWatch Logs
* Lambda metrics
* Error tracking
* Execution duration monitoring

---

## 🔐 Security Best Practices

* Least-privilege IAM roles
* Environment variables for configs
* No hardcoded secrets
* CloudWatch alarms for failures

---

## 📈 Advantages of This Approach

* 💰 Zero infrastructure cost
* ⚡ Highly scalable
* 🧩 Event-driven automation
* 🛠️ Simple to extend (DevSecOps ready)
* 🧠 Excellent learning project

---

## 📚 Use Cases

* Serverless DevOps pipelines
* Automated application deployment
* Event-driven CI/CD
* AWS Lambda mastery project

---

## 🚀 Future Enhancements

* 🔒 Add security scanning Lambda
* 🧪 Add automated test frameworks
* 📦 Docker image build support
* 📊 Add dashboard using CloudWatch
* 🔄 Multi-environment deployment

---




