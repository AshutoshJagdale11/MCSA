# DFS Replication

## Create a Folder on Server1

1. Log in to Server1.
2. Open File Explorer.
3. Navigate to Local Disk (C:).
4. Create a folder named `Repo`.
5. Inside the `Repo` folder, add a file named `Replication`.
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/2fc4fcab-8e94-47b6-92ee-291e1fd2c625" />

## Share the Folder

6. Right-click the `Repo` folder.
7. Select **Properties**.
8. Go to the **Sharing** tab.
9. Click **Advanced Sharing**.
10. Check **Share this folder**.
11. Click **Permissions**.
12. Assign **Full Control** to **Everyone**.
13. Select **Apply**.
14. Click **OK**.
<img width="1919" height="1007" alt="image" src="https://github.com/user-attachments/assets/72f19cb0-9cc6-46c6-ad23-369c0e1a5ff8" />

## Set Folder Permissions

15. Switch to the **Security** tab.
16. Click **Edit**.
17. Select **Users (MICROSOFT\Users)**.
18. Grant **Full Control**.
19. Click **Apply**.
20. Select **OK**.
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/161515e8-ce45-4851-9a3a-0809926bc6a9" />

## Create a Folder on Server2 for Replication

1. Log in to Server2.
2. Open File Explorer.
3. Navigate to Local Disk (C:).
4. Create a folder named `Replication`.

## Share the Folder

5. Right-click the `Replication` folder.
6. Choose **Properties**.
7. Go to the **Sharing** tab.
8. Open **Advanced Sharing**.
9. Enable **Share this folder**.
10. Click **Permissions**.
11. Assign **Full Control** to **Everyone**.
12. Click **Apply**.
13. Select **OK**.
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/cb81fbcf-de3b-49f5-94a5-e81c4f6b1831" />

## Set Permissions

14. Right-click the `Replication` folder again.
15. Go to the **Security** tab.
16. Click **Edit**.
17. Select **Users (MICROSOFT\Users)**.
18. Grant **Full Control**.
19. Click **Apply**.
20. Select **OK**.
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/bf23fe68-fe95-4561-b604-00ee1370c721" />

---

