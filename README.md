# Mendix-Deployment
Documentation about mendix deployment and mendix cloud
# 📘 Deployment Guide: Mendix App + APK Build (Simple & Professional)

This guide explains, in a clear and easy way, how to deploy a Mendix application to the Mendix Cloud and how to build an Android APK for your mobile app.

---

## 1. Open Your App in Mendix Studio Pro

Start by opening your project in **Mendix Studio Pro**.  
This is where you prepare your app before deploying it or building the APK.

---

## 2. Confirm the App Is a Native Mobile App

To generate an APK, your app must be **Native Mobile**.

Check the following:

- The project contains a **Native Mobile** navigation profile  
- Required modules are installed:
  - Native Mobile Resources  
  - Atlas Core  
  - Nanoflow Commons  

If these are present, the app is ready for APK generation.

---

## 3. Build the APK (Android App File)

Mendix uses the **Native Builder** to create the APK.

### Steps:
1. In Studio Pro, open:  
   **App → Build Native Mobile App**
2. Select **Android**.
3. Choose **APK** as the build type.
4. Connect to **Microsoft App Center** using your API token.
5. Click **Start Build**.

The App Center will compile the APK.  
Once finished, download the generated `.apk` file.

---

## 4. Deploy the App to the Mendix Cloud

Your APK needs a backend to connect to.  
This backend is your Mendix app running in the Mendix Cloud.

### Steps:
1. Go to the **Mendix Developer Portal**.
2. Open your application.
3. Navigate to **Environments**.
4. Select the environment (Sandbox, Acceptance, Production).
5. Click **Deploy**.
6. After deployment, click **Start App** or **Restart App**.

Your backend is now live and ready.

---

## 5. Configure the APK to Use Your Cloud Environment

Your APK must know which Mendix Cloud URL to connect to.

### Steps:
1. In the Developer Portal, copy your app URL:  
   Example:  
   `https://yourapp-sandbox.mendixcloud.com`
2. In Studio Pro, open:  
   **App → Build Native Mobile App → Configure**
3. Set the **Runtime URL** to your Mendix Cloud URL.
4. Rebuild the APK if the URL was changed.

This ensures the mobile app communicates with your cloud backend.

---

## 6. Install and Test the APK

After downloading the APK:

- Install it on an Android device  
- Allow installation from unknown sources if required  
- Open the app  
- Test:
  - Login  
  - Navigation  
  - Data loading  
  - Offline features (if used)  

If everything works, your deployment is successful.

---

## 7. Updating the App

Whenever you make changes:

1. Update the app in Studio Pro  
2. Deploy again to the Mendix Cloud  
3. Rebuild the APK  
4. Install the new APK on devices  

---

## ✔️ Summary

You now have:

- A Mendix app deployed to the Mendix Cloud  
- An APK that connects to your cloud environment  
- A repeatable process for future updates  

