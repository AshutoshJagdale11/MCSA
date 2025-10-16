# 🖥️ Workgroup vs Domain in Windows Networking

## 🔹 Workgroup
A **Workgroup** is a peer-to-peer network model where each computer is responsible for its own security and management.  

### ✨ Features:
- No centralized control (each PC manages itself).  
- User accounts are local to each computer.  
- Best suited for **small networks** (≤10 PCs).  
- No domain controller required.  
- Simple setup, usually for home or small offices.  

---

## 🔹 Domain
A **Domain** is a client-server network model managed by a **Domain Controller (DC)**.  

### ✨ Features:
- Centralized management of users, computers, and policies.  
- Users can log in to **any PC in the domain** with a single account.  
- Best suited for **large networks** (corporates, universities).  
- Provides advanced security and group policies.  
- Requires at least one **Domain Controller (Windows Server)**.  

---

## 🔁 Key Differences

| Feature              | Workgroup | Domain |
|----------------------|-----------|--------|
| **Management**       | Each PC manages itself | Centralized via Domain Controller |
| **User Accounts**    | Local on each PC | Stored in Domain Controller |
| **Security**         | Basic, local only | Advanced (Group Policies, Permissions, Encryption) |
| **Scalability**      | Small networks | Large networks |
| **Authentication**   | Local PC login | Domain login (single account across network) |
| **Best For**         | Home / small office | Corporate / enterprise networks |

---
# 💾 NTFS vs FAT32 File System

## 📌 Overview
Windows operating systems support multiple file systems.  
The two most commonly used are **NTFS (New Technology File System)** and **FAT32 (File Allocation Table 32)**.  
Each has its own strengths and limitations.

---

## 🔹 NTFS (New Technology File System)

### ✨ Features:
- Introduced with **Windows NT**.  
- Supports **very large files** (up to 16 TB+ depending on cluster size).  
- Provides **file and folder security** with permissions.  
- Supports **encryption (EFS)** and **compression**.  
- More reliable due to **journaling** (tracks changes to avoid corruption).  
- Commonly used for **Windows system drives** and large storage.  

---

## 🔹 FAT32 (File Allocation Table 32)

### ✨ Features:
- Introduced with **Windows 95 OSR2**.  
- Maximum file size: **4 GB**.  
- Maximum partition size: **2 TB**.  
- No file-level security or encryption.  
- Supported across **Windows, Linux, macOS, consoles, and embedded devices**.  
- Best for **USB drives and cross-platform compatibility**.  

---

## 🔁 Key Differences

| Feature              | NTFS | FAT32 |
|----------------------|------|-------|
| **Full Form**        | New Technology File System | File Allocation Table 32 |
| **Introduced In**    | Windows NT (1993) | Windows 95 OSR2 (1996) |
| **Max File Size**    | 16 TB – 256 TB (depends) | 4 GB |
| **Max Partition**    | 256 TB | 2 TB |
| **Security**         | File/folder permissions, encryption | None |
| **Reliability**      | Journaling (less data loss) | No journaling |
| **Compression**      | Supported | Not supported |
| **Encryption**       | Supported (EFS) | Not supported |
| **Compatibility**    | Modern Windows (limited Linux/macOS) | Almost all OS & devices |
| **Best For**         | Internal/system drives | USB drives, cross-platform use |

---



# 🌐 DNS vs NetBIOS  

## 🔹 DNS (Domain Name System)
- Converts **domain names → IP addresses**.  
- Example: `www.microsoft.com` → `20.112.52.29`  
- Works on **Internet** and modern networks.  
- Uses **hierarchical structure** (Root → TLD → Domain).  
- Port: **53 (UDP/TCP)**.  
- Fast, scalable, and global.  

✅ **Best for:** Internet, large networks, websites.  

---

## 🔹 NetBIOS (Network Basic Input/Output System)
- Converts **computer names → IP addresses** in a LAN.  
- Example: `\\SERVER1` → `192.168.1.10`  
- Works on **local networks (LAN)** only.  
- Flat name system (no hierarchy).  
- Port: **137, 138, 139**.  
- Old technology, mostly replaced by **DNS + Active Directory**.  

✅ **Best for:** Small local networks, legacy systems.  

---

## ⚖️ Difference
| Feature           | DNS 🌍 | NetBIOS 🖥️ |
|-------------------|--------|-------------|
| Usage             | Internet & LAN | Only LAN |
| Naming System     | Hierarchical   | Flat (single level) |
| Port              | 53             | 137–139 |
| Speed & Scalability | High | Limited |
| Status            | Modern, still used | Legacy, less used |

---
# 🌐 DNS Record Types

DNS (Domain Name System) uses different record types to map names with IPs or services.  

---

## 🔹 1. A Record (Address Record)
- Maps a **domain name → IPv4 address**.  
- Example: `www.example.com → 192.168.10.1`

---

## 🔹 2. AAAA Record
- Maps a **domain name → IPv6 address**.  
- Example: `www.example.com → 2001:db8::1`

---

## 🔹 3. CNAME Record (Canonical Name / Alias)
- Points one name to another domain name.  
- Example: `mail.example.com → www.example.com`

---

## 🔹 4. MX Record (Mail Exchange)
- Defines mail servers for a domain.  
- Example: `example.com → mail server = mail.example.com`

---

## 🔹 5. PTR Record (Pointer Record)
- Used in **Reverse Lookup Zone**.  
- Maps **IP address → domain name**.  
- Example: `192.168.10.1 → server1.example.com`

---

## 🔹 6. NS Record (Name Server)
- Defines the **authoritative DNS server** for the domain.  
- Example: `example.com → ns1.example.com`

---

## 🔹 7. SOA Record (Start of Authority)
- Stores main information about the zone (Primary server, admin email, version, refresh time).  
- Example: Zone settings for `example.com`.

---

## 🔹 8. SRV Record (Service Record)
- Defines services like **_ldap, _kerberos** used in Active Directory.  
- Example: `_ldap._tcp.dc._msdcs.example.com`

---

## 🔹 9. TXT Record
- Stores text information (often used for **SPF, DKIM, verification**).  
- Example: `v=spf1 include:_spf.google.com ~all`

---
# 🛠️ Group Policy (GPO)

## 📌 What is Group Policy?
- Group Policy is a Windows feature used to **centrally manage settings** for users and computers.  
- It is mostly used with **Active Directory (AD)**.

---

## 📌 Types of Group Policy
1. **Local Group Policy**
   - Applied to a single computer.  
   - Example: Setting password policy on one PC.

2. **Domain Group Policy**
   - Applied to all users and computers in the domain.  
   - Example: Setting the same wallpaper for all employees.

---

## 📌 Components of Group Policy
- **GPO (Group Policy Object):** A collection of rules.  
- **GPMC (Group Policy Management Console):** The tool used to create/manage GPOs.  
- **OU (Organizational Unit):** A group of users/computers where GPO is applied.  

---

## 📌 Order of Application (Precedence)
👉 **L → S → D → OU**

1. Local Policy  
2. Site Policy  
3. Domain Policy  
4. Organizational Unit (OU) Policy  

*(OU policy has the highest precedence)*


## 📌 Useful Commands
- Open Local Group Policy Editor:
  ```
  gpupdate /force
  ```

---

# 🌐 Forward Lookup Zone

- Maps **Domain Name → IP Address**.  
- Most common DNS zone used on the internet.  
- Record types used:  
  - **A Record** → Maps domain name to IPv4 address.  
  - **AAAA Record** → Maps domain name to IPv6 address.  
  - **CNAME Record** → Alias of another domain name.  
  - **MX Record** → Mail exchange server record.  
- Essential for browsing websites, accessing services, and resolving domain names.  

👉 **Example:**  
`www.nextgen.com → 192.168.10.1`  

# 🔄 Reverse Lookup Zone

- Maps **IP Address → Domain Name**.  
- Performs the reverse function of forward lookup.  
- Record type used:  
  - **PTR Record (Pointer Record)** → Maps IP address back to hostname.  
- Helps in:  
  - **Network troubleshooting** (ping, nslookup, traceroute).  
  - **Email server verification** (anti-spam reverse DNS checks).  
  - **Security auditing** (verify IP belongs to valid domain).  

👉 **Example:**  
`192.168.10.1 → www.nextgen.com`  

✅ **In short:** Reverse Lookup Zone = IP Address → Domain Name  

## 📘 DNS Zones Under Reverse Lookup Zone – Primary

- Contains the **master copy** of DNS records (read/write).  
- Acts as the **authoritative source** for its domain namespace.  
- Only one **Primary Zone** exists per DNS namespace.  
- Stores records like **A, CNAME, MX, PTR, SRV** etc.  
- Changes (add, modify, delete records) can be made **only here**.  
- Can replicate data to **Secondary Zones** for redundancy.


## 📘 Secondary Zone  

### 🔹 What is Secondary Zone?  
- A **read-only copy** of the Primary Zone.  
- Updated through **Zone Transfer**.  
- Provides **redundancy + load balancing**.  
- Cannot be edited directly.  

✅ In short: **Backup of Primary Zone (Read-only)**  


# 🔎 DNS Queries: Recursive vs Iterative

When a client asks DNS to resolve a domain, two types of queries happen: **Recursive** and **Iterative**.

---

## 🔹 Recursive Query
- In recursive, the **DNS server does all the work** for the client.  
- The client (e.g., your PC) asks → "Give me the IP of www.microsoft.com".  
- The DNS server then:
  1. Checks its cache.
  2. If not found, it contacts **Root → TLD → Authoritative DNS** servers.
  3. Finally, it returns the **final answer (IP)** to the client.
- ✅ Client gets only one reply (final IP or error).

**Example:**  
Your PC asks **8.8.8.8 (Google DNS)** for `www.microsoft.com`.  
Google DNS finds the answer and returns only the IP to you.

---

## 🔹 Iterative Query
- In iterative, the **DNS server gives the best answer it knows**.  
- If it doesn’t know the exact IP, it replies with a **referral** (next server to ask).  
- Then **your resolver (client-side or local DNS)** goes step by step:
  1. Ask Root → it says "Go to .com servers".
  2. Ask .com → it says "Go to microsoft.com servers".
  3. Finally, ask microsoft.com → it gives IP.

- ✅ Client may contact multiple DNS servers until it gets the final answer.

**Example:**  
Your PC itself goes Root → TLD → Authoritative DNS step by step until it gets IP.

---

## 📌 Key Difference

| Feature              | Recursive Query | Iterative Query |
|-----------------------|-----------------|-----------------|
| Who finds the final IP? | DNS server does | Client/local resolver does |
| Response              | One final answer | Referrals (next server) |
| Speed                 | Faster for client | Slower (client does more work) |
| Usage                 | Most client PCs use this | Between DNS servers |

---
# 📡 DHCP and DORA Process

---

## 🔹 What is DHCP?
- DHCP = **Dynamic Host Configuration Protocol**  
- It **automatically gives IP addresses** and other network settings to clients (PCs, laptops, phones).  
- No need to assign IP manually.  
- It provides:  
  - **IP Address**  
  - **Subnet Mask**  
  - **Default Gateway**  
  - **DNS Server**  

✅ Makes network management easy.

---

## 🔹 DORA Process (How DHCP Works)

When a client joins the network, it follows the **DORA** process:

1. **D → Discover**  
   - Client broadcasts: "Is there any DHCP server? I need an IP!"  

2. **O → Offer**  
   - DHCP server replies: "Yes, I have an IP for you (e.g., 192.168.10.3)."  

3. **R → Request**  
   - Client says: "I want to use this offered IP (192.168.10.3)."  

4. **A → Acknowledge**  
   - DHCP server confirms: "Okay, this IP is yours. You can use it."  

✅ Now client gets full network config and can communicate.

---

## 📌 Example
- Client joins → Gets IP: **192.168.10.3**  
- Subnet Mask: **255.255.255.0**  
- Gateway: **192.168.10.1**  
- DNS: **192.168.10.2**

---

## 📊 Summary

| Step | Name       | Who Sends | Purpose |
|------|------------|-----------|---------|
| D    | Discover   | Client    | "Who can give me IP?" |
| O    | Offer      | Server    | "Here’s an IP you can use." |
| R    | Request    | Client    | "I want this IP." |
| A    | Acknowledge| Server    | "Confirmed, IP is yours." |

✅ In short: **DORA = How DHCP assigns IP automatically.**


# 💽 MBR vs GPT (Disk Partition Styles)

---

## 🔹 What is MBR?
- **MBR = Master Boot Record**  
- Old partition style (introduced in 1983).  
- Stores partition info in the **first sector of the disk**.  
- Supports **only up to 2 TB disks**.  
- Can have **maximum 4 primary partitions**.  
- Used in **BIOS-based systems**.  

✅ Good for old systems, but limited.

---

## 🔹 What is GPT?
- **GPT = GUID Partition Table**  
- Newer standard (replaces MBR).  
- Supports **disks larger than 2 TB**.  
- Can have **128 partitions** (no need for extended partitions).  
- Stores **multiple copies** of partition data → more reliable.  
- Works with **UEFI-based systems**.  

✅ Modern, more secure, supports big storage.

---

## 📊 Key Differences

| Feature            | MBR                        | GPT                         |
|--------------------|----------------------------|-----------------------------|
| Full Form          | Master Boot Record         | GUID Partition Table        |
| Max Disk Size      | 2 TB                       | 9.4 ZB (theoretical)        |
| Max Partitions     | 4 Primary (or 3 + Extended)| 128 Partitions              |
| Compatibility      | Older systems (BIOS)       | Modern systems (UEFI)       |
| Reliability        | Stores single boot data    | Stores multiple copies      |
| Year Introduced    | 1983                       | 2010+ (with UEFI)           |

---

# 👤 Local Profile vs Roaming Profile in Windows

## 🔹 Local Profile
- Ek **user profile** jo **sirf ek computer** pe banta hai.  
- User ke **Desktop, Documents, aur Settings** locally store hote hain.  
- Agar user dusre PC pe login kare → **profile available nahi hoti**, naya profile ban jaata hai.

### ✨ Pros:
- Fast (local disk pe hota hai).  
- Simple setup.  

### ✨ Cons:
- Settings aur files sirf ek PC tak limited.  

---

## 🔹 Roaming Profile
- Ye profile **server pe store hoti hai** (Active Directory environment).  
- User kisi bhi domain-joined PC pe login kare → **profile server se load hoti hai**.  
- Desktop, Documents, aur Settings **same hote hain har PC pe**.

### ✨ Pros:
- Settings aur data consistent across PCs.  
- Easy management for network admins.  

### ✨ Cons:
- Login/logout slow ho sakta hai (large profile).  
- Network dependency → Server down hone par profile load nahi hogi.  

---

## 🔁 Key Differences

| Feature               | Local Profile                  | Roaming Profile                        |
|-----------------------|--------------------------------|----------------------------------------|
| **Location**          | Local computer disk           | Server (network share)                 |
| **Availability**      | Sirf wahi PC                  | Kisi bhi domain-joined PC              |
| **Setup**             | Simple                        | Requires AD + server setup             |
| **Speed**             | Fast                          | Slow (network dependent)               |
| **Use Case**          | Home / Single PC              | Enterprise / Multiple PC users         |

---

# 📌 Windows Deployment Services (WDS)

## 🔹 What is WDS?
- A Windows Server role used to **install OS over the network** (no CD/USB needed).  
- Clients boot using **PXE (network boot)**.  

---

## 🔹 WDS Components
- **Boot Image** → Starts client PC (WinPE).  
- **Install Image** → Actual Windows OS.  
- **Capture Image** → Capture reference OS.  
- **Discover Image** → For non-PXE boot systems.  

---

## 🔹 How it Works
1. Client PC boots with PXE.  
2. Gets IP from DHCP.  
3. Downloads boot image from WDS.  
4. Selects OS → Installs from install image.  

---


# 📌 Network Load Balancing (NLB)

## 🔹 What is NLB?
- Shares traffic between **multiple servers**.  
- Used for **high availability** and **load distribution**.  

---

## 🔹 Key Points
- If one server fails → others keep working.  
- Works at **Layer 4 (Transport layer)**.  
- Needs at least **2 servers** with static IPs.  

---

## 🔹 Benefits
- High availability  
- Scalability  
- Better performance  

---

## 🔹 Uses
- Web servers  
- Application servers  
- Remote Desktop / VPN servers  


1. **None**
   - Client requests go to **any server randomly**.
   - Best for **stateless apps** (e.g., web browsing).

2. **Single**
   - All requests from the **same client IP** always go to the **same server**.
   - Used when session data is stored locally (e.g., shopping cart).

3. **Class C**
   - Clients from the **same subnet (Class C network)** are directed to the **same server**.
   - Useful for environments with many clients behind NAT.



# 📌 DFS (Distributed File System)

## 🔹 What is DFS?
DFS is a **Windows Server feature** that lets you organize and share multiple folders from different servers into **one logical namespace** (like a virtual folder tree).

---

## 🔹 Types of DFS

1. **DFS Namespace**
   - Provides a **virtual folder structure**.
   - Users see a single path (e.g., `\\domain\dfsroot`) even if files are on different servers.
<img width="492" height="227" alt="image" src="https://github.com/user-attachments/assets/f3e3fb67-12f9-45cd-bca3-782fef68de5b" />


2. **DFS Replication**
   - Keeps copies of folders **synchronized across servers**.
   - Uses **multi-master replication** (changes can happen on any server).

<img width="504" height="224" alt="image" src="https://github.com/user-attachments/assets/1f5d1bd6-ffe9-406f-9318-0d5973da4bad" />

---


# 🧩 What is a Group in Windows Server

A **Group** is a collection of users that helps manage permissions, access, and policies **more easily**.
Instead of assigning permissions to each user individually, you can assign them to a group — and all members inherit those permissions.

---

## 🧠 Types of Groups

### 1. Security Group

* Used to **assign permissions** to resources (files, folders, printers, etc.).
* Example:

  * **Group Name:** `HR-Team`
  * **Members:** HR employees
  * **Access:** Read/Write access to `\\Server1\HRData`

### 2. Distribution Group

* Used for **email distribution** (e.g., in Exchange or Outlook).
* Example:

  * **Group Name:** `All-Employees`
  * **Purpose:** Send one email to everyone at once.

---

## 🌍 Group Scope Types (in AD Domain)

| Scope Type       | Description                                                                        |
| ---------------- | ---------------------------------------------------------------------------------- |
| **Domain Local** | Used to assign access to resources **within the same domain**.                     |
| **Global**       | Contains users from the same domain and can be given permissions in other domains. |
| **Universal**    | Can include users/groups from **any domain** in the forest.                        |

---

## ⚙️ Example

You have 10 users in the **Finance** department.
Instead of granting permissions one by one:

1. Create a group named **Finance_Group**.
2. Add all Finance users to that group.
3. Give **Finance_Group** access to the Finance shared folder.

✅ All members now have the same access automatically.

---

## 🪄 Summary

* Groups make **administration easier and faster**.
* Useful for **security**, **access control**, and **email communication**.
* Best practice: Use **security groups** for permissions and **distribution groups** for communication.
---

# 🌐 Universal, Global, and Domain Local Groups in Active Directory

Active Directory (AD) allows three main types of **group scopes**:
**Universal**, **Global**, and **Domain Local** — each defines **where** and **how** a group can be used in the domain or forest.

---

## 🧩 1. Global Group

* Used to **group users** from the **same domain**.
* Can be assigned permissions in **any domain** within the forest.
* ✅ Best for grouping **users** by department or role.

**Example:**

* Global Group: `Sales_Global`
* Members: Users from `Sales` domain only.
* Access: Can be granted permissions to resources in another domain (e.g., `Finance` domain).

**Usage Tip:**

> Use Global groups to organize **users** with similar job functions.

---

## 🏢 2. Domain Local Group

* Used to assign permissions to **resources** within the **same domain**.
* Can include users and groups from **any domain** in the forest.
* ✅ Best for grouping **resources**.

**Example:**

* Domain Local Group: `HR_Share_Access`
* Members: Users from multiple domains.
* Resource: `\\Server1\HRData` in the HR domain.

**Usage Tip:**

> Use Domain Local groups to assign **permissions** on shared folders, printers, etc.

---

## 🌍 3. Universal Group

* Used to group users, groups, and computers from **any domain** in the **forest**.
* Ideal for **large organizations** with multiple domains.
* Stored in the **Global Catalog**, making them available across all domains.

**Example:**

* Universal Group: `Company_All_Staff`
* Members: Users from HR, IT, and Sales domains.
* Access: Granted to global resources like intranet or shared applications.

**Usage Tip:**

> Use Universal groups for **forest-wide access** or **email distribution lists**.

---

## 🔁 Best Practice (AGDLP Model)

A common Microsoft recommendation for organizing groups:

```
A → G → DL → P
```

* **A** = Accounts (Users)
* **G** = Global Groups
* **DL** = Domain Local Groups
* **P** = Permissions

👉 Add **users** to a **Global Group**,
then add that **Global Group** to a **Domain Local Group**,
and assign **permissions** to the Domain Local Group.

---

## 🧠 Summary Table

| Group Type       | Members From | Permission Scope | Best Used For          |
| ---------------- | ------------ | ---------------- | ---------------------- |
| **Global**       | Same domain  | Any domain       | Organize users         |
| **Domain Local** | Any domain   | Same domain      | Assign resource access |
| **Universal**    | Any domain   | Entire forest    | Cross-domain access    |

---

✅ **In short:**

* **Global = Users**
* **Domain Local = Resources**
* **Universal = Organization-wide access**
---

# 📂 Active Directory Partitions

Active Directory stores its data in different **partitions**.  
Each partition has a specific purpose and replication scope.

---

## 🔑 Types of Partitions

### 1. **Schema Partition**
- Defines **object types** and their **attributes**.  
- Example: User, Computer, Group, Printer.  
- Replicated to **all Domain Controllers** in the **forest**.

---

### 2. **Configuration Partition**
- Contains **forest-wide configuration** data:  
  - Sites  
  - Services  
  - Replication topology  
- Replicated to **all Domain Controllers** in the **forest**.

---


### 3. **Domain Partition**
- Contains **domain-specific data**:  
  - Users  
  - Groups  
  - Computers  
  - Organizational Units (OUs)  
- Replicated only to **Domain Controllers in the same domain**.

---

### 4. **Application Partition**
- Stores **application/service-specific data**.  
- Example: DNS zones (AD Integrated DNS).  
- Replicated only to **specific Domain Controllers**, not the entire forest.

---

## 🧠 Easy Way to Remember
- **Schema** → *What can be created* (structure of objects).  
- **Configuration** → *How AD works* (settings & topology).  
- **Domain** → *What is created* (users, groups, computers).  
- **Application** → *Extra data* (DNS, apps).  

---

## 📌 Example
If the domain is **`cisco.com`**:
- **Schema** defines what a "User" object looks like.  
- **Configuration** defines replication links between servers.  
- **Domain** stores users like *John, HR1, RMG1*.  
- **Application** stores DNS zone data like *cisco.com records*.  

---


# 🖥️ FSMO Roles (Flexible Single Master Operations)

## 🔹 What are FSMO Roles?
- Special roles in **Active Directory** that only **one Domain Controller (DC)** can hold at a time.  
- Prevent conflicts and maintain consistency in the domain/forest.

---

## 🔹 Types of FSMO Roles (5 Total)

### 🏛 Forest-wide Roles (2)
1. **Schema Master**  
   - Controls **AD schema updates** (adding new object types/attributes).  
   - Only ONE in the entire **forest**.  

2. **Domain Naming Master**  
   - Controls **adding/removing domains** in the forest.  
   - Only ONE in the entire **forest**.  

---

### 🏠 Domain-wide Roles (3)
1. **RID Master (Relative ID Master)**  
   - Assigns **unique IDs** to objects (like users, groups).  
   - One per **domain**.  

2. **PDC Emulator (Primary Domain Controller)**  
   - Handles **time sync, password changes, backward compatibility with NT4**.  
   - Important for **user logon**.  
   - One per **domain**.  

3. **Infrastructure Master**  
   - Updates **group-to-user references** across domains.  
   - One per **domain**.  


## 🔹 Quick Shortcut
- **Forest Roles (2):** Schema Master, Domain Naming Master  
- **Domain Roles (3):** RID Master, PDC Emulator, Infrastructure Master  

👉 **2 Forest + 3 Domain = 5 FSMO Roles**

---


# 🔐 VPN (Virtual Private Network)

## 📌 What is VPN?
- A **secure tunnel** between your device and the internet/server.  
- Encrypts data so no one can **spy or steal** information.  
- Helps connect **remote users** to private networks (like office network).  

---

## 🔹 Types of VPN
1. **Remote Access VPN**  
   - Used by employees to connect to office network from home.  
   - Example: Cisco AnyConnect, OpenVPN.  

2. **Site-to-Site VPN**  
   - Connects **two offices/networks** securely over the internet.  
   - Example: Head Office ↔ Branch Office.  

3. **Client-to-Site VPN**  
   - User connects from laptop/PC to company server.  

---

## 📌 What is DirectAccess?
- A feature in **Windows Server (2008 R2 and later)**.  
- Provides **seamless remote connectivity** to corporate network **without manually starting VPN**.  
- Always-on, secure connection using **IPv6 + IPsec**.  

---

## 🔹 How it Works
- When laptop/PC connects to internet → It **automatically connects** to company network through **DirectAccess server**.  
- Uses **IPv6 transition technologies** (6to4, Teredo, IP-HTTPS).  
- Authentication via **Active Directory + Certificates**.  

---
8
