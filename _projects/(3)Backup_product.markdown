---
name: Backup & SaaS Product
tools: [Storage, Backup, SaaS]
image: ../assets/image/hb_disaster_c2.jpeg
description: I employed various approaches to identify the reasons why the SaaS service's retention rate was relatively low and proposed a solution that successfully increased sales. The product includes both on-premises NAS storage and public cloud storage.
---
 ![image](../assets/image/hyperbackup_baremetal.jpeg)   


<br>

# **Backup product- Hyper Backup & C2 Storage**
##### Hybird cloud and SaaS backup product design

> - Duration: Nov 2022 - Jun. 2023
> - Role: Product Manager
> - Team members: 1 UX designers,1 UI designers, 4 SDEs
> - Skills: Product Strategy, Project Management,  Problem solving 


<br>

### **1. Overview and Objectives**
##### **Overview:**

Our product is a NAS (Network Attached Storage), which is an on-premise server. We also provide [C2 Storage](https://c2.synology.com/en-global/storage/overview),a SaaS storage service, that allows customers to backup their on-premise data to the cloud. However, we have encountered a challenge: the retention rate of this service is lower than that of other SaaS services in our company. I aim to devise a solution to increase the retention rate.

##### **Objective:**

Increase the retention rate and user experience, leading to an increase in sales revenue.

<br>

![image](../assets/image/HB_extensive_backup_destinations.png)



### **2. Approach:**
##### **Product Feature Research**

 I did the market research to understand what features our competitors offer and their pricing plans. However, I didn't find a big difference between our product and others.

|                | C2                | Wasabi           | Backblaze         | iDrive                                      | Acronis          |
| -------------- | ----------------- | ---------------- | ----------------- | ------------------------------------------- | ---------------- |
| **Price**      | $6.99 /TB/M       | $5.99 /TB/M      | $5.12 /TB/M       | 10GB free, $1.32 /TB/M                      | $14.99 /TB/M     |
| **Friendly User Interface** | ✓ | ✓ | ✓ | ✓ | ✓ |
| **Security**   | (256-bit AES encryption, 2FA) | (256-bit AES encryption, 2FA) | (256-bit AES encryption, 2FA) | (256-bit AES encryption, 2FA) | Malware & ransomware protection |
| **Customer Support** | Support ticket | Support ticket, phone (limited to Premium plan) | Support ticket, limited chat (Monday – Friday, 9:00 a.m. – 12:00 p.m. and 1:00 p.m. – 5:00 p.m. PST) | Support ticket, chat support, limited phone (Monday – Friday, 6:00 AM to 11:30 PM PST) | Support ticket, live chat, and phone (limited to US, Canada, the UK, Belgium, Singapore, and Australia) |
| **Egress Fee** | × | × | $0.01/GB (Charged when you download files. The first 1 GB of data downloaded each day is free.) | × | × |


##### **Marketing Survey**

| N | Title | Date | Type | Country | Mentioned C2 Storage |
| --- | --- | --- | --- | --- | --- |
| 1 | [6 Solutions to Backup Your Synology NAS Data to Cloud](https://geekflare.com/synology-nas-backup-solutions/) | January 16, 2023 | Article | US | ✓ |
| 2 | [Best NAS backup software. Top NAS backup solutions in 2023.](https://www.baculasystems.com/blog/nas-backup-software-solutions/) | 2023 | Article | US | ✓ |
| 3 | [Top 5 Best Cloud Backup for NAS in 2023](https://www.cbackup.com/articles/best-cloud-backup-for-nas.html) | 2023 | Article | US | ✗ |
| 4 | [4 Best Backup Software for Synology NAS [Pros and Cons]](https://www.easeus.com/backup-utility/best-backup-software-for-synology-nas.html) | Jan 16, 2023 | Article | US | ✗ |
| 5 | [5 Best Cloud Backup Services for NAS – Most Secure in 2023](https://www.websiteplanet.com/blog/best-cloud-backup-nas/) | 2023 | Article | US | ✗ |
| 6 | [5 Best Cloud Backup For Synology in 2023: NAS Backup Providers](https://www.cloudwards.net/best-cloud-backup-for-synology/) | 31 Jul, 2022 | Article | US | ✗ |
| 7 | [5 Best Cloud Backups for Synology in 2023](https://proprivacy.com/cloud/comparison/synology-cloud-backup) | 2023 | Article | US | ✗ |

 ![image](../assets/image/maketing_promotion-comparasion.png)


##### **User survey**


 Conduted user survey. I gathered information from various forums and community discussion and created a questionnaire. When users clicked on the unsubscribe button, a pop-up questionnaire appeared, asking them why they no longer wanted our product. I collected 500 valid results within a month. The results showed that the slow upload speed was the top reason they didn't want to use the product anymore, 35%.
 ![image](../assets/image/Unsubscribe_C2_storage_survey.png)


##### **Data Collection**
 I added the tracking point to the software to record the upload speed. Then I found 20% the uploading speed is less than 1 MB/s. Based on the investment we did before, when the uploading speed is less than 5MB/s, the customers will feel frustrated, as it will take them more than 1 week to backup a 3TB local data.

##### **User Interviews**
   I conducted user interviews and did the research on the social media. I chose 10 users who unsubscribed our product and reached out to them through email and conference calls to ask for their feedback on our product. Some of them told me, the uploading speed is unstable from time to time. When they use our service, it is less than 1 MB/s, however, the speed of our competitor can reach 90MB/s, around 100 times the difference which leads them to change the solution.

<br>

### **3. Proposed Solution**

Strategy: Convert Existing Users to C2 Storage
- Step 1: Convert users of other cloud services.
- Step 2: Convert local NAS/external HDD backup users.

Suggested Solution:
- Product-wise: Make our pricing more compelling by providing more features and increase the tranfer speed.
  - Feature 1: Fastest upload and download speed within the same ecosystem
  - Feature 2: Advanced Ransomware prevention
- Marketing-wise: Improve our visibility to users.
  - Tactic 1: Launch a marketing campaign to increase product awareness of C2 Storage.
  - Tactic 2: Revise the in-product UI to promote the product.
![image](../assets/image/C2_storage_beforeafter_UI.png)
<br>

### **4. Outcome**
We prioritized improving efficiency of uploading backup data. After the product was upgraded, 
- The average speed surge to 5 MB / s
- The retention rate began to recover, moving to 70% within three months.

 