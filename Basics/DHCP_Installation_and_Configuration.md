# 📘 DHCP Installation and Configuration on Server1

---

## 🔹 Part 1: Installing the DHCP Role

### Step 1: Launch Server Manager
1. Click the **Windows Start Button**.  
2. Open **Server Manager**.  

![Server Manager](https://github.com/user-attachments/assets/9ee5bcb0-b63f-4496-9185-c603ecd225bc)  

---

### Step 2: Add the DHCP Role
1. In **Server Manager**, click on **Add roles and features**.  
2. Click **Next** repeatedly until you reach the **Server Roles** section.  
3. Check the box for **DHCP Server**.  

![Add DHCP](https://github.com/user-attachments/assets/a380a22b-bc6b-4c00-82fd-9b9ef9e908a0)

4. Click **Add Features** when prompted, then click **Next**.  
5. Continue clicking **Next** until you reach the **Confirmation** page.  
6. Check **Restart the destination server automatically if required** for convenience.  
7. Click **Install** to start the installation.  

![Install DHCP](https://github.com/user-attachments/assets/ef1630d9-cee8-4135-98f3-9b6ed951290c)

---

### Step 3: Finish Installation
1. Allow the installation to complete.  
2. Click **Close** after it finishes.  
3. In the **Server Manager**, click on the **Flag** icon at the top.  
4. Select **Complete DHCP configuration**.  

![DHCP Config](https://github.com/user-attachments/assets/0689ed90-d1a2-4d82-b7df-a5607f5225f6)

5. Proceed by clicking **Next → Commit → Close**.  

✅ The DHCP role is now installed successfully.

---

## 🔹 Part 2: Configuring DHCP

### Step 1: Open DHCP Management Console
1. Navigate to **Server Manager → Tools → DHCP**.  

![Open DHCP](https://github.com/user-attachments/assets/27c30107-81b9-4ae8-826b-62f7ce7eceac)

---

### Step 2: Create a New DHCP Scope
1. Expand the DHCP server node.  
2. Right-click **IPv4** and select **New Scope**.  
3. Click **Next** to begin.  
4. Enter a name for the scope, e.g., `MicrosoftDomain`.  

![Scope Name](https://github.com/user-attachments/assets/7d8f1ff4-84a9-4597-9b86-39626b1ecaa5)

---

### Step 3: Define IP Address Range
- Set the **Start IP** to `192.168.10.11`.  
- Set the **End IP** to `192.168.10.20`.  

![IP Range](https://github.com/user-attachments/assets/a630a92b-223e-42ab-ab04-6b8667752ea4)

---

### Step 4: Define Excluded IP Addresses
- Exclude the range from `192.168.10.12` to `192.168.10.13`.  

![Exclusions](https://github.com/user-attachments/assets/0578ac16-551a-4ae3-8460-14a5c6507190)

---

### Step 5: Configure Lease Duration
- Use the default lease duration and click **Next**.  

![Lease Duration](https://github.com/user-attachments/assets/12eef570-7b82-4caa-b5bc-3349db9254e0)

---

### Step 6: Setup DHCP Options
- Select **Yes, I want to configure these options now**, then click **Next**.  

![Config Options](https://github.com/user-attachments/assets/acaabcc3-4416-43d6-8ac5-d2382c2abb01)

---

### Step 7: Configure Default Gateway (Router)
- Enter the router IP: `192.168.10.254`.  
- Click **Add**, then **Next**.  

![Gateway](https://github.com/user-attachments/assets/843e174b-b448-457c-8b13-568c66a56788)

---

### Step 8: Configure DNS and WINS Servers
- Leave DNS settings at default (your server’s IP).  
- Click **Next** through DNS and WINS configuration pages.  

---

### Step 9: Activate the DHCP Scope
- Choose **Yes, I want to activate this scope now**.  
- Click **Next**, then **Finish**.  

![Activate Scope](https://github.com/user-attachments/assets/a862f183-a8a8-44b3-88d4-812e5f4292b4)

✅ The DHCP scope is configured and activated.

---

## 🔹 Part 3: Verify DHCP Client Address (on Server2)

### Step 1: Open Command Prompt
1. Press **Windows + R**, type `cmd`, and press **Enter**.  

![CMD](https://github.com/user-attachments/assets/68203c03-e563-4eac-a790-71e05761a907)

---

### Step 2: Check the IP Address
1. Run the command:  
ipconfig

2. Confirm the IP address falls within the DHCP range `192.168.10.11` to `192.168.10.20`.  

<img width="1919" height="1000" alt="Screenshot 2025-09-18 170647" src="https://github.com/user-attachments/assets/2124b2d0-03a4-4961-9923-aadbf772066a" />
