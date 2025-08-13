# cafe-static-website


## 📌 Project Overview
This project involves hosting a static website for a fictional café using **Amazon S3**.  
The site showcases the café's offerings, location, hours, and contact details.  
It follows AWS best practices for **data protection, cost optimization, and disaster recovery**.

---

## 🛠 AWS Services Used
- **Amazon S3** – Website hosting, versioning, lifecycle policies, and cross-region replication
- **IAM** – Role (`CafeRole`) for replication permissions
- **S3 Lifecycle Policies** – Storage class transitions and expiration
- **S3 Bucket Policy** – Public read access for objects

---

## 📂 Architecture
The final architecture contains:
1. **Source S3 Bucket** (us-east-1) – Hosts static site
2. **Destination S3 Bucket** (another AWS region) – Cross-Region Replication target
3. **Versioning** – Prevents accidental overwrites/deletions
4. **Lifecycle Policies** – Cost optimization for older object versions
5. **Bucket Policy** – Grants public read access


---

## 🚀 Features Implemented
### **Challenge 1: Static Website Hosting**
- Created S3 bucket in `us-east-1`
- Enabled **static website hosting**
- Uploaded HTML, CSS, and images
- Applied public bucket policy for read access

### **Challenge 2: Data Protection**
- Enabled **S3 Versioning**
- Tested by modifying `index.html`
- Verified previous versions are retained

### **Challenge 3: Cost Optimization**
- Configured **Lifecycle Rules**:
  - Move previous versions to **S3 Standard-IA** after 30 days
  - Delete previous versions after 365 days

### **Challenge 4: Disaster Recovery**
- Created destination bucket in a different region
- Enabled **Cross-Region Replication**
- Verified new changes replicated successfully


---

## 📜 Bucket Policy Example
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::<YOUR-BUCKET-NAME>/*"
    }
  ]
}
