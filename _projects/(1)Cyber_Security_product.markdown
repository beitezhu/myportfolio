---
name: Security Product
tools: [MFA, SaaS, Cloud]
image: ../assets/image/Cyber-Security-Concept-1.jpeg
description: The design of Multi-Factor Authentication (MFA) and a series of product features was implemented to enhance the security of our cloud service, Synology Account, which has 5 million users. <br>The project involved collaboration with 6 developers over a period of more than 6 months.
---
 ![image](../assets/image/SA_security.jpeg)   


<br>

# **Synology Account**
##### Multi-Factor Authentication product design

> - Duration: Jan 2020 - Jun. 2021
> - Role: Product Manager
> - Team members: 2 UX designers,1 UI designers, 5 SDEs
> - Skills: Product Strategy, Project Management, Market Research

![image](../assets/image/SA_overview.jpeg)  

<br>



### **1. Overview and Objectives**
##### **Overview:**
[Synology Account](https://www.synology.com/en-global/synology-account), a critical SaaS service with over 5 million users, serves as the gateway to all Synology cloud services, including QuickConnect, Active Insight, and C2. The security of Synology Account is paramount, impacting both users and the company. It also facilitates user engagement in Synology Events and community participation.

<br> In 2020, a brute force attack caused data loss and incurred about $100,000 in damages, affecting around 50 NAS users. Although the impact was limited to less than 0.1% of users, it underscored the need for enhanced product security.

##### **Objective:**

To enhance the security of our cloud service, particularly as the integration of products with the Synology Account escalates.

<br>

### **2. Problem Statement**

- **Low Adoption Rate of Two-Factor Authentication (2FA)**: Although we have released 2FA feature for more than 4 years, only a minimal 1% of users have enabled 2FA.
- **User Inaccessibility and Convenience Issues**: Many users face challenges in accessing or managing their 2FA settings, especially in scenarios such as phone loss or OTP inaccessibility. This leads to a reliance on technical support and a general reluctance to engage with existing security measures.
- **Limited Variety in Security Options**: The current security framework primarily relies on OTPs, lacking diversity in authentication methods. This limitation fails to address the varying needs and preferences of a diverse user base.
- **Need for Enhanced User Awareness and Engagement**: There is a significant gap in user understanding and involvement regarding their account's security settings. Users often do not regularly check or update their security preferences, partly due to the lack of a user-friendly interface.
- Certain legacy portals are restricted to OTP for 2FA, pending upgrades by users.

 
<br>

### **3. Approach:**

- Introduce diverse methods for straightforward multi-factor authentication (MFA) setup.
- Foster user engagement in enabling two-factor authentication (2FA) through education on its significance.
- Strengthen account security, independent of 2FA activation.

##### **Out of Scope**
- Mandatory 2FA implementation remains outside our current scope, focusing instead on voluntary adoption supported by user education and enhanced security features.

<br>

### **4. Research Methodology**

##### **Survey and Inquiry:**

- Collected 500 responses identifying the top three reasons for low MFA setup: perceived cumbersomeness, uncertainty about setup, and fear of being locked out post-setup.

##### **User Interviews:**

- Discovered issues with double password entry inconvenience and fears of losing access due to accidental app deletion.

##### **Competitive Analysis:**

- Examined Google, Microsoft, and Adobe’s security login methods. Noted each offers more than two 2FA methods, including OTP and phone push notifications.


| Feature                          | Google                                   | Microsoft                                       | Adobe                      |
|----------------------------------|------------------------------------------|-------------------------------------------------|----------------------------|
| Two-Factor Authentication (2FA)  | Yes                                      | Yes                                             | Yes                        |
| Authentication Methods           | OTP, Push Notification, U2F Key          | OTP, Push Notification, Physical Security Key   | OTP, SMS, Email            |
| Backup Methods                   | Backup Codes, Secondary Email            | Secondary Email, Security Questions             | Recovery Email             |
| User Interface                   | User-friendly, Intuitive                 | Intuitive, Comprehensive                        | Simple, Straightforward    |
| Recovery Options                 | Email, Phone                             | Email, Phone, Security Questions                | Email                      |
| Additional Security Features     | Advanced Protection Program              | Microsoft Authenticator App                     | Adobe Account Access       |





 ![image](../assets/image/SA-research.jpeg)  
<br>



### **5. Proposed solution**

 <table>
        <tr>
            <th>Proposed Solution</th>
            <th>Pros</th>
            <th>Cons</th>
        </tr>
        <tr>
            <td>New Login Method: "Approve Signin" Feature</td>
            <td>
                <ul>
                    <li>Enhances security against phishing by diminishing password reliance</li>
                    <li>Convenient for users: simple approval via phone</li>
                    <li>Accessible for those who find traditional 2FA methods cumbersome</li>
                </ul>
            </td>
            <td>
                <ul>
                    <li>Requires stable internet connectivity</li>
                    <li>Necessitates downloading an additional Synology Secure Signin app</li>
                    <li>Learning curve: relatively new approach in the market</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Overview Page: Simplified Interface for Security Settings</td>
            <td>
                <ul>
                    <li>User-friendly interface improves understanding of security settings</li>
                    <li>Promotes user engagement in security practices</li>
                    <li>Highlights the importance of security to users</li>
                </ul>
            </td>
            <td>
                <ul>
                    <li>Development demands time and resources</li>
                    <li>Needs regular updates for new features and threats</li>
                    <li>Users less likely to check settings regularly as it requires web service login</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Abnormal Sign-in Notification: Login Attempt Alerts</td>
            <td>
                <ul>
                    <li>Increases awareness of unauthorized access attempts</li>
                    <li>Enables prompt response to potential breaches if they didn't log in</li>
                </ul>
            </td>
            <td>
                <ul>
                    <li>Risk of notification fatigue in users</li>
                    <li>Potential for false alarms leading to undue concern</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Abnormal Sign-in Compulsory 2FA: Mandatory 2FA for Abnormal IPs</td>
            <td>
                <ul>
                    <li>Enhances security level by enforcing 2FA on suspicious login attempts</li>
                </ul>
            </td>
            <td>
                <ul>
                    <li>Can be cumbersome for users, especially if falsely identified as abnormal</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Security Key Integration</td>
            <td>
                <ul>
                    <li>Provides a highly secure, physical authentication method</li>
                    <li>Useful for users without smartphone access</li>
                    <li>Adds a new security option for users</li>
                </ul>
            </td>
            <td>
                <ul>
                    <li>Incurs additional costs for users to acquire keys</li>
                    <li>Not essential for all, potentially confusing as an unfamiliar option</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Legacy Portal: Update with Advanced 2FA Options</td>
            <td>
                <ul>
                    <li>Upgrades outdated systems to current standards</li>
                    <li>Extends protection to more users</li>
                </ul>
            </td>
            <td>
                <ul>
                    <li>Significant development and testing required</li>
                    <li>Challenges with compatibility in legacy systems</li>
               </ul>
            </td>
        </tr>
</table>
 
 <br>


### **6. Product MVP Requirements**


| N | Component              | Feature                                                       | Priority |
|---|------------------------|---------------------------------------------------------------|----------|
| 1 | Visual Appearance      | Design of Overview Page to Identify Account Security Level    | P1       |
| 2 | Backend                | Backend Development for "Approve Signin" Service              | P1       |
| 3 | Mobile App Development | Mobile App for Push Notification (Approve Signin)             | P1       |
| 4 | Visual Appearance      | User Interface for "Approve Signin" Feature Setup             | P1       |
| 5 | Backend                | Update and Secure Legacy Portals with Advanced 2FA            | P1       |
| 6 | Backend/Frontend       | Backup Method Implementation                                  | P1       |
| 7 | Visual Appearance      | User Interface for Security Key Setup                         | P2       |
| 8 | Backend                | Integration of Security Key as a Login Option                 | P2       |
| 9 | Backend/Frontend       | Abnormal Activity Notification: Login IP History Tracking and Display | P2 |
| 10| Backend                | Integration with App Push Notification Service                | P2       |
| 11| Backend                | Email Notification System                                     | P2       |
| 12| A/B Test               | Testing "Approve Signin" Feature and OTP Setup Complete Rate  | P3       |
| 13| A/B Test               | Testing User-Friendliness and Incentive of Overview Security Section | P3 |
| 14| Internal Controls      | Monitoring and Feedback Tools                                 | P3       |
| 15| Backend/Frontend       | Privacy Data Deletion Features                                | P3       |
| 16| Backend                | SMS Notification Integration                                  | P3       |

<br>
##### **Priority Definitions:**

- **P1 (Required for Launch)**: Essential features that are critical for the launch.
- **P2 (Expected for Launch)**: Important features that are planned for the launch but can be deferred if necessary.
- **P3 (Desired for Launch)**: Additional features that would enhance the product but are not crucial for the initial launch.

<br>

### **7. Released Product**
It takes about one year to release all three stages of the security features. The results of the feature release are impressive. 
- The 2FA setup rate increased from 1% to 15%.
- The number of support tickets decreased by 80%, saving significant time for tech support engineers and preventing potential data leaks.
![image](../assets/image/SA_overview_UI.png)
![image](../assets/image/SA_security_UI.png)
  
  
