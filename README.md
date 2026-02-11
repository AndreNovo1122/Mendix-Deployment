# 📦 Mendix Deployment Package, Cloud Deployment & Licensed Node Guide

This documentation provides a clear and structured overview of:

- How to create a **deployment package (.mda)** in Mendix  
- How to publish an application to the **Mendix Cloud**  
- How to deploy to a **licensed (paid) node**  
- How to troubleshoot common deployment issues  

Additional platform‑level information (Control Center, Cloud, Kubernetes, etc.) is included in the **Appendix**.

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
- **CI/CD pipelines**

This process creates a **stable build** of the application based on the current repository state.

## ⚠️ Important Notes:
Before creating the package, ensure:

- The **version tag** matches the Mendix version used in the project  
- The project is clean and error‑free  

---

# 3. Publishing the App to the Mendix Cloud (Free App / Sandbox)

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
   - Deploy it to the Sandbox environment  

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

Código

### 4. Errors in the Error Console
The app **must not have any errors** before publishing.

---

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

# 7. Deploying to a Licensed Node (Paid Node)

Deploying to a **licensed node** in the Mendix Cloud is similar to publishing a free app, but there are important differences.  
A licensed node represents a **dedicated, paid environment** with its own resources, security, and lifecycle management.

This section explains how to deploy an application to a licensed Mendix Cloud node.

---

## 7.1 What Is a Licensed Node?

A licensed node is a paid Mendix Cloud environment that includes:

- Dedicated CPU/RAM resources  
- Production‑grade infrastructure  
- Acceptance + Production environments  
- Monitoring, logging, and metrics  
- Backup & restore  
- SLA and support  
- Custom domain support  
- HTTPS certificates  
- Scaling options  

A licensed node is created when:

- You purchase a Mendix Cloud license  
- You create a new licensed app in the Mendix Portal  
- Mendix provisions a **Node** (environment container)

---

## 7.2 Key Differences vs Free App Deployment

| Feature | Free App | Licensed Node |
|--------|----------|----------------|
| Environment type | Sandbox only | Acceptance + Production |
| Resources | Shared | Dedicated |
| Scaling | No | Yes |
| Backups | No | Yes |
| Custom domains | No | Yes |
| Monitoring | Limited | Full (Metrics, Alerts, Logs) |
| CI/CD | Limited | Fully supported |
| Deployment method | Publish from Studio Pro | Upload MDA or CI/CD pipeline |

---

## 7.3 Deployment Methods for Licensed Nodes

Licensed nodes support **three** deployment methods:

### **1. Publish from Studio Pro (Acceptance only)**  
Works similarly to free apps, but publishes to the licensed node.

### **2. Upload an MDA package manually**  
Using the Mendix Portal → Environment → Deploy.

### **3. Automated CI/CD pipeline**  
Using Mendix Deploy API or GitHub Actions / Azure DevOps.

---

# 7.4 Deploying to a Licensed Node Using Studio Pro

This is the simplest method.

### Steps:

1. Open the project in **Mendix Studio Pro**  
2. Ensure:
   - Project is in **Production Mode**
   - No errors in the Error Console
   - You are logged in with the correct Mendix account
3. Click **Publish** (or the cloud icon)
4. Studio Pro will:
   - Build the deployment package  
   - Upload it to the licensed node  
   - Trigger a deployment  
5. In the Mendix Portal, you will see the deployment appear under:

Environments → Acceptance / Production

Código

<img width="1808" height="776" alt="image" src="https://github.com/user-attachments/assets/8c97abf2-bc41-41a6-aae4-0fbc3e18907a" />

### ⚠️ Important:
Publishing directly from Studio Pro **always deploys to the Acceptance environment**, not Production.

Production deployments must be promoted manually.

---

# 7.5 Deploying an MDA Package to a Licensed Node (Manual Upload)

This is the **recommended** method for production‑grade deployments.

### Steps:

1. Create the `.mda` package in Studio Pro (F7)
2. Go to the Mendix Portal:
App → Environments → Acceptance or Production

Código
3. Click **Deploy**

<img width="388" height="126" alt="image" src="https://github.com/user-attachments/assets/73e285b4-2e8d-442a-aedd-90acff1d6fa5" />

4. Upload the `.mda` file  
5. After upload, click **Start Application**  
6. Monitor logs and startup status

### Why use this method?

- Full control over versioning  
- Safer for production  
- Works with CI/CD  
- No dependency on Studio Pro login  

---


# 7.6 Promoting from Acceptance to Production

**Important:** Promotion from Acceptance to Production is **not guaranteed** to be a single automatic button in every Mendix tenant. Promotion is either **manual** (upload the same `.mda` to Production) or **automated via CI/CD**. Treat promotion as an operational step that may require manual intervention or a configured pipeline.

![imagem](https://github.com/user-attachments/assets/e9b9ea75-e944-40e9-9909-a1791eb25252)

### Promotion Methods

| Method | How it works | Requirements | Notes |
|--------|--------------|--------------|-------|
| **Manual upload to Production** | Upload the same `.mda` used in Acceptance directly to the Production environment (`App → Environments → Production → Deploy`). | Deploy permissions; the `.mda` artifact | Full control; recommended when you must guarantee the exact artifact. |
| **Portal promotion (when available)** | Some tenants expose a **Promote** or **Transport to Production** action from the Acceptance environment. | Tenant must support this feature; deploy permissions | Not available in all tenants; verify in your tenant before relying on it. |
| **Automated CI/CD** | Pipeline builds the `.mda` and deploys to Production using the Mendix Deploy API or CI/CD tools (GitHub Actions, Azure DevOps, Jenkins). | Deploy API credentials; Node ID; updated pipeline configuration | Recommended for repeatable production workflows; update pipelines if nodes are reassigned. |

### Manual Promotion Steps

1. **Confirm artifact consistency**  
   - Ensure the `.mda` used in Acceptance is the same artifact you will deploy to Production.  
2. **Generate or retrieve the `.mda`**  
   - Build in Studio Pro (F7) or download the artifact used in Acceptance.  
3. **Open the Portal**  
   - Navigate to `App → Environments → Production`.  
4. **Deploy**  
   - Click **Deploy** and upload the `.mda`.  
5. **Start and monitor**  
   - Start the application and monitor logs, health checks, and startup messages.  
6. **Have a rollback plan**  
   - Prepare a rollback artifact or snapshot and document steps to revert if needed.

### CI/CD Promotion Steps

1. **Build**  
   - Pipeline builds the `.mda`.  
2. **Deploy**  
   - Pipeline uses the Deploy API or configured actions to deploy to Production.  
3. **Smoke tests**  
   - Run automated smoke tests in Acceptance; on success, proceed to Production.  
4. **Update pipeline secrets**  
   - If nodes are reassigned, update Node ID, Deploy API credentials, and environment URLs in the pipeline.

### Pitfalls and Recommendations

- **Studio Pro publishes only to Acceptance** — it does not publish directly to Production.  
- **Do not assume a Portal Promote button exists** — verify tenant capabilities.  
- **Ensure artifact parity** — always deploy the same `.mda` to avoid environment drift.  
- **Permissions** — Production deploys require appropriate roles (Technical Contact or deploy rights).  
- **CI/CD updates** — reassigning nodes requires immediate updates to Node ID and credentials in pipelines.  
- **Rollback readiness** — always have a tested rollback plan and backups before promoting.

### Quick Pre‑Promotion Checklist

- **Artifact**: `.mda` verified and checksum matched.  
- **Permissions**: Deploy rights confirmed for the operator.  
- **Environments**: Acceptance tests passed; health checks green.  
- **Backups**: Database and configuration backups available.  
- **CI/CD**: Pipelines updated with correct Node ID and credentials if needed.  
- **Monitoring**: Logs and alerts configured for Production post‑deploy.  

**Summary**  
Promotion to Production is either **manual** (upload the `.mda`) or **automated via CI/CD**. The Portal may offer a Promote action in some tenants, but this is not universal — treat promotion as an operational step that must be planned and controlled.


---

# 7.7 CI/CD Deployment to Licensed Nodes

Licensed nodes support automated deployment using:

- Mendix Deploy API  
- GitHub Actions  
- Azure DevOps  
- Jenkins  
- GitLab CI  

Typical pipeline:

1. Pull code from Git  
2. Build MDA using Mendix Build API  
3. Upload MDA to Acceptance  
4. Run automated tests  
5. Promote to Production  

---

# 7.8 Requirements for Licensed Node Deployment

Before deploying, ensure:

- The node is **active**  
- You have **Deploy Permissions**  
- The app is in **Production Security Mode**  
- No errors in the project  
- JDK path is correct  
- You are logged into the correct Mendix account  

---

# 7.9 Troubleshooting Licensed Node Deployment

### ❌ “You do not have permission to deploy”
You need the role:  
**Technical Contact** or **App Team Member with Deploy Rights**

### ❌ “Node is not active”
- Check license status  
- Check if the node is suspended or expired

### ❌ “Deployment failed during startup”
Check:

- Environment variables  
- Constants  
- Database connection  
- Scheduled events  
- Logs under **Environment → Logs**

<img width="776" height="621" alt="image" src="https://github.com/user-attachments/assets/e135bda5-34e2-413c-9c0d-e6c78a7d7c1b" />

---

# ✔️ Summary: Licensed Node Deployment

Licensed nodes provide:

- Production‑grade infrastructure  
- Multiple environments  
- Manual and automated deployment options  
- Promotion workflows  
- Full monitoring and logging  

Deployment can be done via:

- Studio Pro (Acceptance only)  
- Manual MDA upload  
- CI/CD pipelines  


# 8. Creating Licensed Nodes & Linking Applications (Critical Concepts)

Deploying to a licensed node requires understanding how nodes are created, how they become associated with an application, and how to safely detach or reassign an app from an existing node.  
This section explains the full lifecycle of a licensed node and the pitfalls to avoid.

---

# 8.1 How Licensed Nodes Are Created

Licensed nodes are **not created automatically**, even if your organization has purchased licenses.  
A licensed node is provisioned when you create a **Licensed App** in the Mendix Portal.

### Steps to create a licensed node:

1. Open the Mendix Portal  
2. Click **Create App**  
3. Select **Create a Licensed App**  
4. Choose:
   - Region (EU/US)  
   - Mendix Cloud version  
   - App name  
5. Confirm creation

### What happens behind the scenes:

- A dedicated **Node** is provisioned  
- Acceptance + Production environments are created  
- Monitoring, backups, logs, and metrics are enabled  
- A unique **Node ID** is generated  
- The node becomes permanently associated with the app

> A licensed node is **always created from the app**, not the other way around.

---

# 8.2 How Apps Become Linked to Nodes

When a Licensed App is created:

- The app is automatically linked to the node  
- The node is automatically linked to the app  
- This relationship is **1-to-1**  
- A node cannot host multiple apps  
- An app cannot be linked to multiple nodes  

You can verify the link under:

App → Environments → Node Details

Código

---

# 8.3 How to Remove an App From an Existing Node

This is required when:

- A node was created under the wrong app  
- You want to reuse a node for a different app  
- You want to delete an app but keep the node  
- You want to migrate an app to a new node  

### Important rule:
A licensed node **cannot be reassigned** until the original app is **fully detached**.

### Steps to detach an app from a node:

1. Open the Mendix Portal  
2. Open the app currently linked to the node  
3. Navigate to:
App → Settings → General

Código
4. Scroll to **Linked Node**  
5. Click **Unlink Node** (requires permissions)

### After unlinking:

- The app loses access to the node  
- The node becomes **Unassigned**  
- The app becomes a normal project without environments  
- No data is deleted  
- The node becomes available for reassignment  

---

# 8.4 Assigning a Node to a Different App

Once a node is unlinked, it can be assigned to another app.

### Steps:

1. Open the target app  
2. Navigate to:
App → Environments

Código
3. Click **Assign Existing Node**  
4. Select the unassigned licensed node  
5. Confirm the assignment

### Behind the scenes:

- The node is reattached  
- Acceptance + Production environments become available  
- The app inherits the node’s infrastructure  

---

# 8.5 Pitfalls & Critical Warnings

### ⚠ Pitfall 1 — You cannot link a node if the app already has a node  
Unlink the existing node first.

### ⚠ Pitfall 2 — You cannot unlink a node while environments are running  
Stop Acceptance/Production before unlinking.

### ⚠ Pitfall 3 — You cannot assign a node if:
- The node is suspended  
- The license is expired  
- The node is still linked to another app  
- You lack permissions (requires Technical Contact)

### ⚠ Pitfall 4 — Studio Pro publish always targets Acceptance  
You cannot publish directly to Production.

### ⚠ Pitfall 5 — Deleting an app leaves the node orphaned  
It will appear under:
Control Center → Other Apps → Unassigned Nodes

Código

### ⚠ Pitfall 6 — CI/CD pipelines break if the node is reassigned  
You must update:
- Deploy API credentials  
- Node ID  
- Environment URLs  

---

# 8.6 How to Verify That an App and Node Are Correctly Linked

Verify the link in three places:

### 1. App → Environments  
Shows Acceptance + Production.

### 2. App → Settings → General  
Displays:
Linked Node: <Node ID>

Código

### 3. Control Center → Mendix Cloud  
Shows the app under the node’s resource group.

> If all three match, the link is correct.

---

# 8.7 How to Safely Move an App to a New Node (Recommended Procedure)

This is the safest and most consistent migration workflow:

1. Create a new Licensed App (new node)  
2. Unlink the old node from the old app  
3. Link the new node to the new app  
4. Deploy the MDA to the new node  
5. Test in Acceptance  
6. Promote to Production  
7. Archive or delete the old app if needed  

This avoids:

- Orphaned nodes  
- Broken pipelines  
- Environment inconsistencies  
- Data loss  

---

# 8.10 Real‑World Process: Creating a Project, Reassigning a Node, and Linking the App

In Mendix Cloud, licensed nodes do **not** appear automatically, even if your company has purchased licenses.  
Nodes only become available after Mendix Support enables them for your account.  
This section explains the real operational workflow used in production environments.

---

## 8.10.1 Why Nodes Do Not Appear Automatically

Even with multiple paid licenses:

- Nodes **do not show up** in the “Assign Existing Node” list  
- Nodes **are not visible** in the Control Center  
- Nodes **cannot be created manually**

### ✔ Nodes only appear after opening a Mendix Support ticket

Support will ask:

- Which app will use the node  
- Which region  
- Which cloud version  
- Which license  

Only after this step does the node become available for association.

---

## 8.10.2 The Correct Workflow (Processual, Not Technical)

This is the **actual** process used in real Mendix Cloud operations.

### Step 1 — Create the new project (empty)

Creating a new app generates:

- The project  
- The repository  
- The app entry in the Portal  

But **no node is linked yet**.

---

### Step 2 — Go to the app that currently owns the licensed node

Open the app currently linked to the node you want to reuse.

---

### Step 3 — Dissociate the node from that app

Navigate to:

App → Settings → General → Linked Node → Unlink Node

Código

Requirements:

- Stop the environment first  
- You must have **Technical Contact** permissions  

After unlinking:

- The node becomes **Unassigned**  
- The old app loses Acceptance/Production  
- The node becomes available for reassignment  

---

### Step 4 — Go to the new project created in Step 1

Open the new app that should receive the node.

---

### Step 5 — Associate the node to the new app

Navigate to:

App → Environments → Assign Existing Node

Código

Select the unassigned node.

After this:

- The new app gains Acceptance + Production  
- The node is now linked to the new project  
- The app can now deploy to that node  

---

### Step 6 — Only now you can deploy the MDA

Once the node is linked:

- Upload the `.mda` manually  
- Or publish from Studio Pro (Acceptance only)  
- Or use CI/CD  

Before linking the node, deployment is impossible because:

- The app has no environments  
- Studio Pro has nowhere to publish  
- The Portal cannot accept an MDA  

---

## 8.10.3 Critical Pitfalls to Avoid

### ⚠ Nodes do not appear unless Support enables them  
Even with licenses purchased.

### ⚠ Apps only “see” the node they are linked to  
If you have 100 nodes, the app sees **only the one linked to it**.

### ⚠ You cannot unlink a node while environments are running  
Stop Acceptance/Production first.

### ⚠ CI/CD breaks when you change nodes  
Update:
- Node ID  
- Deploy API credentials  
- Environment URLs  

### ⚠ Studio Pro always deploys to Acceptance  
Never to Production.

### ⚠ Deleting an app leaves the node orphaned  
It will appear under:
Control Center → Other Apps → Unassigned Nodes

Código

---

## 8.10.4 Summary of the Operational Workflow

1. Create the new project (empty)  
2. Go to the app that currently owns the node  
3. Dissociate the node  
4. Go to the new project  
5. Associate the node  
6. Deploy the MDA  
7. Promote to Production if needed  

This is the **correct**, **safe**, and **supported** way to move nodes between apps in Mendix Cloud.

# 8.11 Visual Diagram — Licensed Node Reassignment Workflow (Table Version)

| Step | Action | Description | Result |
|------|--------|-------------|---------|
| **1** | **Create New Project** | Create a new empty Mendix app in the Portal. | Project exists but **no node is linked**. |
| **2** | **Open App That Owns the Node** | Go to the app currently linked to the licensed node. | You can manage the node from this app. |
| **3** | **Stop Environments** | Stop Acceptance/Production before unlinking. | Node becomes eligible for dissociation. |
| **4** | **Unlink Node** | `App → Settings → General → Linked Node → Unlink Node` | Node becomes **UNASSIGNED**. Old app loses environments. |
| **5** | **Open the New Project** | Go to the new app created in Step 1. | Ready to receive the node. |
| **6** | **Assign Existing Node** | `App → Environments → Assign Existing Node` | Node becomes linked to the new app. Acceptance/Production appear. |
| **7** | **Deploy MDA** | Upload MDA manually, or publish from Studio Pro (Acceptance only), or use CI/CD. | App is deployed to the licensed node. |
| **8** | **Test in Acceptance** | Validate functionality and configuration. | App is ready for promotion. |
| **9** | **Promote to Production** | Use “Transport to Production” in the Portal. | Production environment updated with the same MDA. |

---

## ✔ Summary

This table represents the **only correct, safe, and supported** workflow for:

- Moving a licensed node between apps  
- Reusing nodes  
- Preparing a new project to receive a node  
- Ensuring deployments work correctly  

It complements the detailed explanations in sections **8.1 → 8.10**.



