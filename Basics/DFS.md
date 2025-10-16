# DFS Installation & Configuration Lab

## Preparation

- Ensure you have domain admin rights (or similar permissions).
- **Server1**, **Server2**, and **Client1** should all be domain-joined (domain used: `microsoft.com`).
- Confirm File and Printer Sharing is enabled and network communication works between all devices.
- If requested during setup, enabling automatic restart for servers is recommended for smoother lab progress.

---

# Step 1 — Add DFS Roles (Repeat on Server1 & Server2)

**Instructions for Server1 (do the same for Server2):**

1. Sign in to **Server1** with an administrator account.
2. Open **Server Manager**.
3. Select **Add roles and features**.
4. Click **Next** until reaching the **Server Roles** screen.
5. Expand **File and Storage Services → File and iSCSI Services**.
6. Select **DFS Namespaces**.
7. Select **DFS Replication**.
8. Optionally, enable **File Server Resource Manager**.
9. Optional: Enable auto-restart for the server (recommended for labs).
10. Click **Install** and wait for the process to finish.

**Screenshot — Selecting roles:**  
![Select DFS Roles](https://github.com/user-attachments/assets/140b19f0-a239-4485-949b-a50986c0320f)

**Screenshot — Install and restart:**  
![Install Complete / Restart Option](https://github.com/user-attachments/assets/0e7c9607-55a2-4170-9360-b266653fda21)

**Repeat the same DFS role installation steps on Server2:**  
![Same installation on Server2](https://github.com/user-attachments/assets/113dbf73-42c2-420e-813d-8531ec8a16f4)

---

# Step 2 — Create & Share Folders

Create and share two folders, one on **Server2** (`C:\hr1`) and one on **Client1** (`C:\hr2`) using `Everyone` Full Control (safe only for testing; avoid in production).

## Server2 — Folder Setup

1. Log in to **Server2**.
2. Open **File Explorer → This PC → Local Disk (C:)**.
3. Make a new folder named `hr1` (`C:\hr1`).
4. Right-click `hr1` → **Properties** → **Sharing** tab.
5. Choose **Advanced Sharing**.
6. Enable **Share this folder**.
7. Click **Permissions**.
8. Assign **Full Control** to **Everyone** (for lab).
9. Apply and confirm with **OK**.

**Screenshot — hr1 folder:**  
![Create hr1 on Server2](https://github.com/user-attachments/assets/24e7ce83-3c80-4d64-b435-1cb02c30cfb6)

**Screenshot — share permissions:**  
![Share Permissions - Everyone Full Control](https://github.com/user-attachments/assets/515875b3-c87f-4b3b-902b-d3ef85092dc7)

## Client1 — Folder Setup

1. Sign in to **Client1**.
2. Create folder `hr2` on drive C: (`C:\hr2`).
3. Right-click > **Properties → Sharing → Advanced Sharing**, and tick **Share this folder**.
4. Set permissions for **Everyone** to **Full Control** (for demo).
5. Apply and click **OK**.

**Screenshot — hr2 folder:**  
![Create hr2 on Client1](https://github.com/user-attachments/assets/abe55937-cc15-47f5-a171-5cfb0ad0c4af)

> **Note:** In real environments, use AD security groups and specific NTFS permissions instead of `Everyone`.

---

# Step 3 — Create Domain-based DFS Namespace (on Server1)

1. On **Server1**, go to **Server Manager → Tools → DFS Management**.
   - This opens the DFS management console.

**Screenshot — DFS Manager:**  
![Open DFS Manager](https://github.com/user-attachments/assets/b9d62c65-e41f-47ec-86e0-915ebd964b09)

2. In DFS Management, right-click **Namespaces** → **New Namespace**.

**Screenshot — create new namespace:**  
![New Namespace](https://github.com/user-attachments/assets/45af4d91-f22e-4230-836b-1596b8e04523)

3. Specify **server1** as the namespace host, and proceed by clicking **Next**.

**Screenshot — namespace host selection:**  
![Select Namespace Server (server1)](https://github.com/user-attachments/assets/533f8571-18aa-4ec2-936d-512899dc0b51)

4. Input namespace name as **HR**—the path will be: `\microsoft.com\HR`. Continue.

**Screenshot — namespace named HR:**  
![Enter Namespace Name: HR](https://github.com/user-attachments/assets/adbac635-f151-4927-937a-b3abcce5673b)

5. Choose **Domain-based namespace**, confirm and proceed.

**Screenshot — select domain-based namespace:**  
![Domain-based Namespace selection](https://github.com/user-attachments/assets/ace27f39-931d-48ee-a8e6-d16e9db054df)

6. Complete the wizard by clicking **Create**.

**Screenshot — namespace success:**  
![Namespace created successfully](https://github.com/user-attachments/assets/86c6288d-30e0-4337-8c1e-fcada16496a0)

---

# Step 4 — Add Namespace Folders and Set Folder Targets

Add two folders to the `\microsoft.com\HR` namespace: `hr1` points to `\server2\hr1`, `hr2` points to `\client1\hr2`.

## Add Folder `hr1` (target: `\server2\hr1`)

1. In DFS Management, expand `\microsoft.com\HR`.
2. Right-click `HR` → **New Folder**.
3. Name folder `hr1`.
4. Add the target by clicking **Add**, type in `\server2\hr1`, and confirm.

**Screenshot — add hr1 target:**  
![Create folder hr1 under namespace and add target](https://github.com/user-attachments/assets/b2161584-73bb-4ceb-be55-3abfcf0b1af8)

## Add Folder `hr2` (target: `\client1\hr2`)

1. Again, right-click `\microsoft.com\HR` → **New Folder**.
2. Name the folder `hr2`.
3. Add folder target `\client1\hr2` with **Add** and confirm.

**Screenshot — add hr2 target:**  
![Create folder hr2 under namespace and add client target](https://github.com/user-attachments/assets/899ad7e3-65d8-487e-9ad3-a487d2e3d278)

> Optionally, enable DFS Replication to synchronize folder content (see step 6 below).

---

# Step 5 — Test Namespace & Folder Accessibility

1. On any domain-joined PC (Server1, Server2, Client1), press **Windows Key + R**.
2. Enter `\microsoft.com` and hit Enter.
3. The `HR` namespace should show, containing `hr1` and `hr2`.

**Screenshot — access namespace:**  
![Run \microsoft.com to view namespace](https://github.com/user-attachments/assets/0389f2fb-f808-45cb-b84a-7a1f6e7e2405)

4. Opening `HR` then selecting `hr1` or `hr2` should direct you to `\server2\hr1` and `\client1\hr2`.

**Screenshot — namespace folders display:**  
![Namespace shows hr1 and hr2 folders](https://github.com/user-attachments/assets/4bb12368-d63a-4b16-8c85-2706104f71a7)

> Confirm on Server2 and Client1 as well for proper connectivity and permissions.

---

# Step 6 — Optional: Set Up DFS Replication

> Use DFS Replication for automatic file sync between servers.

1. In DFS Management, right-click **Replication** → **New Replication Group**.
2. Select **Multipurpose replication group**, then click **Next**.
3. Add replication members (e.g., Server2, etc).
4. Choose folder to replicate (such as `C:\hr1`), define schedule and bandwidth.
5. Complete the wizard, then check DFS Replication logs for status.

**Tip:** Check **Event Viewer → Applications and Services Logs → DFS Replication** for errors.

---

# Troubleshooting & Best Practices

- **Access issues:** Double check both sharing and NTFS permissions; these must allow proper user access.
- **Missing namespace:** Ensure namespace server (Server1) is online, domain resolves, and namespace is domain-based.
- **Target unreachable:** Verify network links, firewalls, and that the share exists (`\server2\hr1`, `\client1\hr2`).
- **Replication problems:** Use DFS Replication logs and make sure servers use RPC/SMB.
- **Security advice:** Always use designated AD security groups and the least required NTFS permissions outside of labs.

---
