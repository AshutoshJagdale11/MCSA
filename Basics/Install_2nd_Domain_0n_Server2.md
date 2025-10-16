# Second Server Domain Configuration (Server2)

## Installing Active Directory Role

1. Open **Server Manager**.  
2. Click **Add Roles and Features**.  

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/55421e07-716f-425b-ae4f-dbb0b49a2d61" />

3. Continue clicking **Next** until you reach the **Server Roles** page.  
4. Check the box for **Active Directory Domain Services**.  

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/b94517f8-e393-43cd-b0a9-fc986b8d9486" />

5. Click **Add Features** in the prompt.  

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/8559471f-883f-410b-a0b7-705ab1e8c58b" />

6. Optionally, check **Restart the destination server automatically if required**.  
7. Click **Install**.  

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/47a42f87-b494-42ff-91ed-1d51402eec72" />

8. After installation, click the **flag icon** in Server Manager.  
9. Select **Promote this server to a domain controller**.  

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/e88dbf6d-44ea-46e8-8bd5-38a3468be675" />

10. The Active Directory Domain Services Configuration Wizard will open.  
11. Choose the deployment option:  
    - **Add a domain controller to an existing domain**.  
12. Provide the domain information for the existing domain:  
    - Domain: `microsoft.com`.  
13. Click **Next**.  

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/6e9f4735-5b38-4795-9de4-bcefad8e0f1e" />

14. Configure Domain Controller capabilities and site information:  
    - Select **DNS Server**.  
    - Choose **Global Catalog**.  
15. Site name: `Default-First-Site-Name`.  
16. Set the Directory Services Restore Mode password:  
    - Password: `pass@123`.  
    - Confirm password: `pass@123`.  

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/637b4031-c676-46bb-8316-c710f61de273" />

17. On the DNS options screen, click **Next**.  
18. Specify additional replication options:  
    - Replicate from: `server1.microsoft.com`.  
19. Click **Next**.  

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/38f4d42b-a17b-43d0-b794-d746d6c1a84e" />

20. Leave default paths for AD DS database, log files, and SYSVOL.  
21. Click **Next**.  
22. Click **Install** to finish the promotion.  

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/b4e585e6-dd72-4462-b67f-ff4a742cfc3d" />

---

## Creating a New User

1. Open **Server Manager**.  
2. Click **Tools**.  
3. Select **Active Directory Users and Computers**.  

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/bdcf85c5-4dc6-420a-aa30-62d46f6e30f6" />

4. Expand and select the domain `microsoft.com`.  
5. Right-click on the **Users** container.  
6. Choose **New → User**.  

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/e0a6bcac-2c8d-4c97-b0b4-25b335fc0f2e" />  
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/d325600b-415e-4a25-a892-24e32f40d660" />  
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/4f0fc233-1c06-4c69-aee3-8be7bfd0c275" />

---

## Verification

1. On the primary domain controller (Server1), open **Server Manager**.  
2. Click **Tools** → **Active Directory Users and Computers**.  
3. Open `microsoft.com` domain and navigate to **Users**.  
4. Confirm the presence of the newly created user, e.g., `Adity`.  

<img width="1919" height="1006" alt="image" src="https://github.com/user-attachments/assets/3edca8b0-a75c-403d-84c1-98355a4b4654" />
