# Windows Server Administration Project

## 🖥️ Project Overview
This project demonstrates the setup and administration of a Windows Server network environment, including Active Directory, DNS, DHCP, WDS, WSUS, RODC, GPO management, child domains, and web servers.

[Project](./1.png)
---

## 🧱 Topology Summary
- A new VM was created and configured with Windows Server.
- The server was promoted to a **Primary Domain Controller** for domain: `iti.local`.
- The following services were added:
  - Active Directory Domain Services (AD DS)
  - Domain Name System (DNS)
  - Dynamic Host Configuration Protocol (DHCP)
  - Windows Deployment Services (WDS)
  - Windows Server Update Services (WSUS)

---

## 🧪 Requirements & Implementations

### ✅ User Restrictions via GPO:
- **User1@iti.local** is restricted from logging into **PC1** on **Fridays**.
- **User2@iti.local**:
  - Can log into **PC1**.
  - Can **remotely access PDC** (without being Domain Admin) via GPO permissions.
- **User3@iti.local**:
  - Finds **WinRAR** automatically installed on login to PC1 via GPO.
  - Cannot access **Flash Drives** or **Control Panel**.
  - Has a custom **ITI wallpaper** set via GPO.
- **User4@iti.local**:
  - Same restrictions and desktop setup as User3.

---

### 🧩 GPOs Applied:
- `xControlPanel`
- `xFlashMemory`
- `DesktopLogoWallPaper`

Applied specifically to SmartVillage OU and excluded for other users.

---

## 🔐 Read-Only Domain Controller (RODC)
- **User8** can only log into RODC and shut it down but cannot create users.
- **User9@iti.local** can:
  - Log into **PC3** (joined to domain).
  - **Replicate password** to RODC as part of `Account Operators`.

---

## 🌐 Child Domain: `Alexandria.iti.local`
- **PC2** joined to child domain.
- **User6** created on child DC.
- **Web Server** created with IIS, hosting two websites:
  - `www.web1.com`
  - `www.web2.com`

### DNS Setup:
- Added new DNS zones and hosts for both websites in the respective domains.
- **User6** can access `www.web2.com`.
- **User7** can access `www.web1.com` from **PC4** (added to Managers OU).

---

## 🔧 Web Server Access
- **User7** granted administrative access to WebServer.
- Remote Desktop enabled and port **3389** opened in firewall.
- Confirmed full remote administrative control.

---

## 🧑‍💼 HR Department Delegation
- In `Alexandria.iti.local`, an **OU named HR-Department** was created.
- **User7** delegated permission to **create and delete users** inside the OU.

---

## 💡 Lessons Learned
- Important note: Never remove the **Default Website** in IIS—disable it instead if needed.

---

## ✅ Result
A fully functional multi-domain Windows Server network with user restrictions, GPOs, child domains, DNS zones, web hosting, and delegated permissions, showcasing skills in enterprise server administration.

---

