# Mendix-Deployment
Documentation about mendix deployment and mendix cloud
# 📦 Mendix Deployment Package, Cloud Deployment & Control Center Guide

This documentation provides a clear and structured overview of:

- How to create a **deployment package (.mda)** in Mendix  
- How to publish an application to the **Mendix Cloud**  
- How to navigate and use the **Mendix Control Center**  
- How to manage apps, licenses, environments, private cloud and Kubernetes  
- How to monitor the health of your organization and applications  

---

# 1. Creating a Deployment Package (MDA)

A **deployment package (.mda)** is a file that contains everything Mendix needs to run your application on a server (on‑prem, Docker, Mendix Cloud, etc.).

## 🔹 Steps to create the deployment package:

1. In Mendix Studio Pro, press **F7**  
   or go to:  
   **App → Create Deployment Package**

   <img width="1920" height="1032" alt="image" src="https://github.com/user-attachments/assets/f59781a7-fba1-4a80-a118-09cb7f6d4a14" />

2. A **versioning** window will appear, where you define:
   - The package version  
   - The version tag  
   - (Optional) CI/CD pipeline integration  

   <img width="718" height="579" alt="image" src="https://github.com/user-attachments/assets/0a310e6f-f983-48f2-a066-fb4a9ba10960" />

3. Click **OK**.

4. Mendix will generate the package and automatically download the `.mda` file.

---

# 2. What Is the Deployment Package Used For?

The `.mda` file can be used for:

- **On‑prem Mendix App Server**
- **Docker image of the Mendix Runtime**
- **Importing into another Mendix Cloud environment**
- **ENSA / QA / PROD environments**
- **CI/CD pipelines that pull code from the repository**

This process creates a **stable build** of the application based on the current repository state.

## ⚠️ Important Notes:
Before creating the package, ensure:

- The **version tag** matches the Mendix version used in the project  
- The project is clean and error‑free  

---

# 3. Publishing the App to the Mendix Cloud

After creating the deployment package, you can publish directly to the Mendix Cloud.

## 🔹 Steps:

1. In Studio Pro, click **Publish**  
   (the app **must not be running**).

   <img width="760" height="458" alt="image" src="https://github.com/user-attachments/assets/c67a4d68-fd90-42fa-a9a4-df5791488a33" />

2. Make sure you are **logged in** with the correct Mendix account.

3. Mendix will:
   - Generate dependencies  
   - Create a package  
   - Upload it to the Cloud  
   - Deploy it to the selected environment  

4. If everything goes well, you will see:  
   **“Your app is published!”**

---

# 4. Alternative: Cloud Icon Button

In the top‑right corner of Studio Pro, there is a **cloud icon**.

This button performs the same actions as Publish:

- Generates the package  
- Uploads it to the cloud  
- Deploys automatically  

---

# 5. Common Errors and How to Fix Them

## ❌ **Error: “Something went wrong” when publishing**
<img width="392" height="148" alt="image" src="https://github.com/user-attachments/assets/cea50bb3-475c-4881-8d0c-9b2d6f97ef6a" />

### 1. Missing permissions
Check if you have access to the app:  
**Mendix Portal → Apps → Company Apps**

### 2. Incorrect JDK directory
Verify the JDK path in:  
**Edit → Preferences → JDK Directory**

### 3. Wrong Security Mode
To publish to the cloud, the project **must** be in:

Project Security → Production Mode


### 4. Errors in the Error Console
The app **must not have any errors** before publishing.

---

<img width="624" height="138" alt="image" src="https://github.com/user-attachments/assets/9fd4e184-9678-4b01-8437-2f8a1fee5f33" />

# 6. Summary of the Process

1. Create the deployment package (F7)  
2. Confirm versioning and dependencies  
3. Verify permissions and JDK path  
4. Enable **Production Mode**  
5. Ensure there are no errors  
6. Click **Publish** or the cloud icon  
7. Wait for: **“Your app is published!”**

<img width="539" height="222" alt="image" src="https://github.com/user-attachments/assets/588a790c-d043-4217-b723-5b0fd677c9ab" />

---

# 🧭 7. Mendix Control Center — Overview

The **Control Center** is the central management dashboard for your Mendix organization.

Here you can view:

- Deployed apps  
- Private cloud apps  
- Licenses  
- Users  
- Cluster health  
- Security  
- Company‑level settings  

---

# 8. Mendix Cloud (Licensed Environments)

Inside Control Center → **Mendix Cloud**, you can see:

### 🔹 Running Apps
Applications currently deployed and active.

### 🔹 Not Deployed
Nodes created but without a deployment.

### 🔹 Private Cloud Apps
Apps associated with your account and deployed on:

- Azure  
- AWS  
- GCP  
- Registered Kubernetes clusters  

### 🔹 Connected Mode
If the cluster is registered and synchronized:

- CI/CD integration becomes available  
- Logs and metrics are visible  
- Deployments can be controlled from Mendix  

---

# 9. Cloud (All Apps)

Shows **all applications** created by your organization.

Admins can see everything.

---

# 10. Other Apps

Apps that:

- Are deployed outside Mendix Cloud  
- Are running in private cloud  
- Were migrated to external environments  

---

# 11. Deactivated Apps

Apps that were:

- Removed from the registry  
- Detached from the repository  
- Archived  
- Migrated to private cloud  

---

# 12. Health Dashboard

Displays the health of environments.

### Important:
- This **does not monitor the app itself**  
- It monitors the **cluster**, similar to Prometheus  
- Shows:
  - Critical errors  
  - Node status  
  - Availability  

---

# 13. Deployed Apps Overview

Shows all deployed applications.

### Free Apps
- Status  
- App ID  
- Last deployment  

### Licensed Keys
Apps that:

- Use paid licenses  
- Run in private cloud  
- Require a license key if not in connected mode  

---

# 14. People (Users & Permissions)

Here you can see:

- All organization members  
- Roles and permissions  
- Who can deploy  
- Who can manage environments  

### Creating users
This is where new members are added.

---

# 15. Company → Company Settings

Configure:

- Company domains  
- Security policies  
- Global organization settings  

### Note:
Admins can only be added if their email matches the company domain.

---

# 16. Company Dashboard

Shows:

- License status  
- App status  
- Mendix versions used  
- History of app creation  
- Security  
- Deprecated apps  

---

# 17. Mendix Admins

Shows:

- Who has deployment permissions  
- Who is an admin  
- Who can manage licensed environments  

---

# 18. Marketplace

Allows you to:

- Import modules  
- Update dependencies  
- Manage reusable components  

---

# 19. Project Categories

Organize apps by:

- Team  
- Client  
- Department  
- Project type  

---

# 20. Apps Grid (Top Menu → Apps)

As an admin, you can:

- Access all apps  
- Import apps into Studio Pro  
- View details, environments, permissions  

---

# 21. Deployment Section (Grid → Deployment)

This is where licensed environments are managed.

### When you create a licensed app:
- A **node** is created  
- That node becomes the deployment target  
- A valid license must be active  

You then import the app into that node.

---

# 22. Mendix on Kubernetes (Private Cloud)

In **Mendix on Kubernetes**, you can manage private clusters:

- Azure AKS  
- AWS EKS  
- Google GKE  
- Oracle Cloud  
- Any Kubernetes‑compatible cluster  

### Cluster Manager
Allows you to:

- Register clusters  
- Enable connected mode  
- Integrate CI/CD  
- Synchronize with the Mendix account  

---

# ✔️ Final Summary

With this guide you can:

- Create deployment packages (.mda)  
- Publish apps to the Mendix Cloud  
- Manage apps, licenses and environments  
- Administer private cloud and Kubernetes  
- Monitor cluster health  
- Control users and permissions  
- Organize and maintain your entire Mendix infrastructure  



