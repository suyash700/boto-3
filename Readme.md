# AWS Automation using Python (boto3)

📌 Overview

This practical demonstrates how to automate AWS infrastructure and IAM security auditing using Python and boto3.

### 🔹 Part A – VPC Components Automation

Created core networking components programmatically:

VPC

Subnet

Internet Gateway

Route Table

### 🔹 Part B – IAM Security Automation

Built a script to:

Identify over-privileged IAM users

Remove dangerous policies

Apply a restricted LimitedAccessPolicy


-----------------------
-------------------

## 🟢 Part A — VPC Setup using boto3
🥇 Step 1 — Create VPC

Created a new VPC with CIDR block 10.0.0.0/16.

Resource Name: Practical-VPC

Code Execution

<img width="1920" height="1080" alt="Screenshot (211)" src="https://github.com/user-attachments/assets/553ac03d-600c-475b-9f6a-8db1fb4f5cfe" />



<img width="1914" height="968" alt="Screenshot 2026-02-11 193326" src="https://github.com/user-attachments/assets/88e0f34d-6230-4d04-bb9e-8b4943542cf8" />

## 🥈 Step 2 — Create Subnet

Used the existing VPC ID to create a public subnet.

Resource Name: Practical-Public-Subnet

Explanation

Reused the VPC ID instead of creating a new VPC.

Prevented duplicate resources.

📸 Screenshot:

<img width="726" height="157" alt="Screenshot 2026-02-11 193338" src="https://github.com/user-attachments/assets/f2ffd075-6610-4f78-967f-339253f0aea2" />

<img width="675" height="84" alt="Screenshot 2026-02-11 193356" src="https://github.com/user-attachments/assets/7a2a8f10-5677-48a0-bb33-b8bb1eda3a94" />

<img width="1919" height="921" alt="Screenshot 2026-02-11 193430" src="https://github.com/user-attachments/assets/c055c2a1-c1dc-405b-b48e-00a7af9fcf90" />

-------------------
--------------------

## 🥉 Step 3 — Create and Attach Internet Gateway

Created an Internet Gateway and attached it to the VPC.

Resource Name: Practical-IGW

Purpose

Enable internet access to resources inside the VPC.

📸 Screenshot:

<img width="841" height="306" alt="Screenshot 2026-02-11 193444" src="https://github.com/user-attachments/assets/015f0c88-7d5d-4e01-a882-0702a71a721c" />

<img width="719" height="109" alt="Screenshot 2026-02-11 193458" src="https://github.com/user-attachments/assets/95c88527-3313-406b-abb4-0aac398a89f5" />

<img width="1910" height="918" alt="Screenshot 2026-02-11 193545" src="https://github.com/user-attachments/assets/7713774b-4d90-4adc-9e65-d29c544b2063" />


🏅 Step 4 — Configure Route Table

Created a route table and added route:

0.0.0.0/0 → Internet Gateway

Resource Name: Practical-RouteTable

Purpose

Allow outbound internet traffic.

📸 Screenshot:

<img width="972" height="627" alt="Screenshot 2026-02-11 193612" src="https://github.com/user-attachments/assets/cfff35ee-4c3e-4b3c-b6d1-cd97cab06d3f" />

<img width="724" height="168" alt="Screenshot 2026-02-11 193624" src="https://github.com/user-attachments/assets/8e3b8205-4f5c-4966-9026-a2dab91d1604" />

<img width="1915" height="919" alt="Screenshot 2026-02-11 193649" src="https://github.com/user-attachments/assets/48b889fe-a552-4129-a04a-07e27e33915a" />

________________________

### ⚠️ Important Practical Note

During development:

The VPC was created once.

The generated vpc_id was reused in later steps.

This avoided multiple VPC creations during testing.

___________________________
___________________________

## 🔵 Part B — IAM Audit and Remediation (boto3)
🧠 Objective

Identify IAM users with excessive permissions and automatically remediate.

🥇 Step 1 — Scan IAM Users

The script:

Lists all IAM users.

Checks for:

AdministratorAccess managed policy.

Inline policies containing "Action": "*".

📸 Screenshot:

<img width="982" height="517" alt="Screenshot 2026-02-11 193930" src="https://github.com/user-attachments/assets/a7ba394e-cc5c-4679-a3b5-311e1bedf109" />

<img width="1919" height="917" alt="Screenshot 2026-02-11 194032" src="https://github.com/user-attachments/assets/7e912da9-5cb7-4ec5-a09a-b5e501671e42" />

## 🥈 Step 2 — Create LimitedAccessPolicy

Created a custom managed policy allowing:

EC2 Describe access

S3 ReadOnly access

📸 Screenshot:

<img width="887" height="577" alt="Screenshot 2026-02-11 193753" src="https://github.com/user-attachments/assets/76530f98-fded-44d8-8737-bb2ecdcd33cc" />

<img width="894" height="549" alt="Screenshot 2026-02-11 193922" src="https://github.com/user-attachments/assets/76ce88b1-24f0-42cf-93b9-4e9e78822816" />

<img width="1916" height="960" alt="Screenshot 2026-02-11 193859" src="https://github.com/user-attachments/assets/9e74a872-2cde-4608-83ee-31eaeebfec04" />


## 🥉 Step 3 — Detach Dangerous Policies

Automatically detached:

<img width="843" height="681" alt="Screenshot 2026-02-11 194134" src="https://github.com/user-attachments/assets/3afa9ee8-b25d-4f54-9c17-f51075975b03" />

<img width="649" height="421" alt="Screenshot 2026-02-11 194107" src="https://github.com/user-attachments/assets/b5202531-bc28-429f-a373-385e5e0e06b2" />

<img width="504" height="191" alt="Screenshot 2026-02-11 194116" src="https://github.com/user-attachments/assets/8f08025b-aa1c-4006-bd7e-78ab924810fa" />


## 🏅 Step 4 — Attach Safe Mode Policy

Attached:

<img width="1918" height="922" alt="Screenshot 2026-02-11 194056" src="https://github.com/user-attachments/assets/ffbe790f-b794-408a-8f44-49a1bef14391" />

<img width="458" height="123" alt="Screenshot 2026-02-11 195738" src="https://github.com/user-attachments/assets/b224e332-51ae-4ebd-a5b8-b6778f5c7df8" />



______
_____

## 💡 Learning Outcomes

Automated AWS networking using Python.

Implemented least-privilege IAM strategy.

Built DevOps-style remediation automation.

Used tagging and structured naming conventions.

________________

## Author : Suyash Dahitule

