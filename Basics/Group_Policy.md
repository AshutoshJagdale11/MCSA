# 🛠️ Active Directory – Organizational Units, Users & Group Policy Setup

This tutorial provides detailed steps to **create Organizational Units (OUs)**, **add users**, and **enforce Group Policies** within **Active Directory**, accompanied by screenshots.

---

## 📌 Step 1: Launch Active Directory Users and Computers  
1. Click **Tools** in the Server Manager.  
2. Choose **Active Directory Users and Computers**.  

![Active Directory](https://github.com/user-attachments/assets/2f1b0073-db2a-43ce-bbbb-4cd7f89d4704)

---

## 📌 Step 2: Create Organizational Units (OUs)  
We will set up three OUs named **HR**, **RMG**, and **PROJECT**.

1. Right-click on the domain `microsoft.com`.  
2. Select **New → Organizational Unit**.  

![New OU](https://github.com/user-attachments/assets/60b90eb4-dd38-46c1-9382-b1a1d4a15f38)

3. Enter the name `HR` → Click **OK**.  

![HR OU](https://github.com/user-attachments/assets/c8c72ac9-ef48-4c71-9e66-f344b500ec2d)

➡️ Repeat these steps to create **RMG** and **PROJECT** OUs.

---

## 📌 Step 3: Add Users to OUs  
Example: Creating the user **HR1** inside the **HR OU**.

1. Right-click on **HR OU** → **New → User**.  

![New User](https://github.com/user-attachments/assets/05ed8b49-1459-4809-8dda-83f89d1e5a86)

2. Fill in details:  
   - First Name: `HR1`  
   - Logon Name: `HR1`  

![HR1 User](https://github.com/user-attachments/assets/e74589ae-3f17-49fd-91c3-0658939f972e)

3. Set the password:  
   - Enter password: `Pass@123`  
   - Check **Password Never Expires** → Click **Next**  

![Password](https://github.com/user-attachments/assets/fd7d4e47-8daa-46a8-afd9-e62d45fda89d)

➡️ Repeat similarly for **HR2, HR3**.  
➡️ Also create users **RMG1, RMG2, RMG3** and **PROJECT1, PROJECT2, PROJECT3**.  

Your OUs and users will appear like this:  

![OU Users](https://github.com/user-attachments/assets/e4c79de7-e0c7-489b-9ea8-cc764060fd90)

---

## 📌 Step 4: Apply Group Policy at the Domain Level  
Example: Disable the **Run** option from the Start Menu for all users across the domain.

1. Open **Group Policy Management**.  

![GPO](https://github.com/user-attachments/assets/656f0b47-baf7-475b-b988-1c6f87f688d8)

2. Expand: `Forest: microsoft.com → Domains → microsoft.com`.  
3. Right-click **Default Domain Policy** → Choose **Edit**.  

![Edit GPO](https://github.com/user-attachments/assets/ee2f9a9f-3a2c-43a3-a33d-562ebec98adf)

4. Navigate through:  
   - **User Configuration → Policies → Administrative Templates → Start Menu and Taskbar**.  
   - Select **Remove Run menu from Start Menu**.  

![Run Menu](https://github.com/user-attachments/assets/7c79b2fb-96eb-4d75-87c5-af609beb622d)

5. Enable the setting → Click **Apply → OK**.  

![Enable Policy](https://github.com/user-attachments/assets/103f5442-a60d-44b5-a9bc-483bfb2c45b0)

---

## 📌 Step 5: Confirm Group Policy on Client  
1. Log in to **Server2** using user **HR1** credentials:  
   - Username: `HR1`  
   - Password: `Pass@123`  

![Login](https://github.com/user-attachments/assets/6fff2f59-8b15-40d4-8f76-c9ef18d69169)

2. Attempt to open **Run (Win + R)**.  

![Run](https://github.com/user-attachments/assets/8a2a7428-c9b9-44e1-acf2-27857e8c7fbb)

3. An error message will appear, showing the **Run** option is disabled.  

![Error](https://github.com/user-attachments/assets/0cca57c8-f99c-4b53-bab8-9c9be22f48f1)

---

## 📌 Step 6: Assign OU-Level Policy (Specifically for HR)  
1. In **Group Policy Management**, right-click the **HR OU**.  
2. Select **Create a GPO in this domain, and Link it here**.  

![New GPO](https://github.com/user-attachments/assets/c37ff1f8-7c1a-415f-b30c-f87485e75c01)

3. Name the policy `HRPOLICY` → Click OK.  

![HR Policy](https://github.com/user-attachments/assets/1cdfebea-6984-4cc3-9d12-ac7affb05e73)

4. Right-click on `HRPOLICY` and select **Edit**.  

![Edit HR Policy](https://github.com/user-attachments/assets/d159bf4c-e7b1-4000-9ea2-7d08b3771ead)

5. Follow the same path:  
   - **User Configuration → Policies → Administrative Templates → Start Menu and Taskbar**.  
   - Configure **Remove Run menu from Start Menu** to **Disable**.  

![Disable Policy](https://github.com/user-attachments/assets/970b3ef4-8e1b-46ad-9b86-a00991744b66)

6. Click **Apply → OK** to save.  

![Disable Apply](https://github.com/user-attachments/assets/645b54ab-7039-405b-8d66-e44836567680)

---

## 📌 Step 7: Validate OU-Level Policy

### HR User  
1. Log in to **Server2** as user `HR1`.  
2. If the policy is not yet applied, force update it by running the command:  

gpupdate /force

<img width="1919" height="1004" alt="Screenshot 2025-09-23 172503" src="https://github.com/user-attachments/assets/e5db63e4-7f11-4fb1-a3dc-43bd1b7c7f82" />

3. Open the Start Menu, right-click, and click **Run**.  
<img width="1917" height="1079" alt="image" src="https://github.com/user-attachments/assets/11ec8aca-2b35-4b21-8eec-c67b57db0f3e" />

> ✅ The **Run** command is available because the policy now allows it for HR users.

### RMG User  

1. Log in to **Server2** as user `RMG1` with password `Pass@123`.  
![RMG1 login](https://github.com/user-attachments/assets/09842651-f293-4059-ae1d-aae508fde26f)

2. Try to open **Run (Win + R)** — nothing will happen or you will see an error.  
![Open Run](https://github.com/user-attachments/assets/8a2a7428-c9b9-44e1-acf2-27857e8c7fbb)

3. The error message appears when attempting to open Run:  
![Run error](https://github.com/user-attachments/assets/0cca57c8-f99c-4b53-bab8-9c9be22f48f1)

> ❌ The policy does not apply here, so Run remains disabled for RMG users.

---
