# AWS Resource Tracker Shell Script

## 📌 Project Overview
This project is a **real-time shell script** used to **track AWS resource usage**.

### 🔥 Why Use This Script?
When multiple developers have access to AWS, unnecessary resources may be created leading to **increased costs**. This script **monitors** active resources and **generates a report** helping DevOps engineers track resource usage efficiently.

## 🚀 Features
- **Lists AWS resources**:
  - 🖥️ EC2 Instances
  - ☁️ S3 Buckets
  - 🏗️ Lambda Functions
  - 🔐 IAM Users
- **Filters EC2 instances to show only Instance IDs**
- **Saves report to a file**
- **Can be scheduled with Cron Jobs for automation**
- **Uses AWS CLI and `jq` for JSON parsing**

---

## 📋 Prerequisites
Before running the script, ensure the following:

### 🔧 System Requirements
- **AWS CLI** installed & configured (`aws configure`)
- **Bash shell** (Linux/macOS)
- **`jq`** installed (for parsing JSON)
- **Correct AWS IAM permissions** (read access to AWS resources) If using IAM Account

### 🔗 AWS CLI Setup Guide  
🔹 **Watch my tutorial on AWS CLI Setup and Usage** 👉 [LinkedIn Post](https://www.linkedin.com/posts/thegagankapoor_aws-cli-ec2-setup-activity-7292855727080054785-z9Op?utm_source=share&utm_medium=member_desktop&rcm=ACoAAFcwqqYBw0quEruUZMAfYQQX55vo42H15V0)  

---

## 📜 Installation & Setup

### 1️⃣ Install Unzip & AWS CLI
```bash
sudo apt install unzip
```

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```
Then configure it:
```bash
aws configure
```
Provide:
- AWS Access Key - 
- AWS Secret Key - 
- Default region - Press Enter and it will select Default

## Create a file
```bash
vim aws_resource_tracker.sh
```

---

## 📝 Script Code (`aws_resource_tracker.sh`)

```bash
#!/bin/bash

##########################
# Author: Gagan
# Date: 06-Feb-2025
#
# Version: v1
#
# This script reports AWS resource usage
##########################

set -x  # Enable debug mode

# AWS S3
# AWS EC2
# AWS Lambda
# AWS IAM Users

echo "Fetching list of S3 buckets..."
aws s3 ls >> resourceTracker

echo "Fetching list of EC2 instances..."
aws ec2 describe-instances | jq '.Reservations[].Instances[].InstanceId' >> resourceTracker

echo "Fetching list of Lambda functions..."
aws lambda list-functions >> resourceTracker

echo "Fetching list of IAM Users..."
aws iam list-users >> resourceTracker
```

---

## 🏃 Running the Script
1️⃣ **Give Execute Permission**  
```bash
chmod 700 aws_resource_tracker.sh
```
2️⃣ **Run the script**  
```bash
./aws_resource_tracker.sh
```
3️⃣ **Check the output in `resourceTracker` file**
```bash
cat resourceTracker
```

---

## 🕒 Automating with Cron Job
To schedule this script to run every day at **4:30 PM**, add this to your crontab:
```bash
crontab -e
```
Add:
```
30 16 * * * /path/to/aws_resource_tracker.sh

```
## 📸 Script Output  
Below is the sample output of the script execution:  

![Screenshot_985](https://github.com/user-attachments/assets/ed274850-0078-4ffa-8efd-e2c8ae3ce0e0)



---

## 🛠️ Troubleshooting
### ❌ Issues You Might Face
1. **AWS CLI not installed?**  
   ➜ Install it using the above link if you are using linux
2. **`jq` not found?**  
3. **Wrong Access Key Details**  
   ➜ Ensure your Access Key details are right

---

## 📚 Learnings & Takeaways
- **Automation is powerful**: Cron jobs eliminate manual work.
- **AWS CLI is useful**: Helps track cloud resources efficiently.
- **Always check dependencies** (`jq`, AWS CLI must be installed).

---

## 🎯 Final Thoughts 

This was my **first hands-on DevOps project** and I learned a lot! 🚀  

- At first **AWS CLI felt overwhelming** but after exploring and testing different commands, I got comfortable with it.  
- Using **Bash scripting** to automate AWS resource tracking gave me a **real-world understanding** of how DevOps engineers monitor cloud usage.  
- I faced **small challenges** like missing dependencies (`jq`) and also made some typo errors but fixing them **boosted my confidence**.  

💡 If you're a **beginner**, I highly recommend trying this project. It helps you **understand AWS, Bash scripting, and automation**.  

---




