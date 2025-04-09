<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Post-Install Configuration</h1>
This tutorial outlines the post-install configuration of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Configure osTicket, post-installation](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Post-Install Configuration Objectives</h2>

# osTicket Post-Installation Configuration

This document provides essential **post-installation configuration steps** after osTicket has been successfully installed on a Microsoft Azure VM running Windows 10.

---

## ✅ What You Should See After Installation

After completing the web installer at `http://<your-ip>/osTicket/setup`, you should see a success page confirming that the system is ready.

Now it's time to lock down and configure your helpdesk!

---

## 🔒 1. Delete Setup Directory

Immediately delete the `/setup` directory to prevent unauthorized access:

```bash
C:\inetpub\wwwroot\osTicket\setup
```

Right-click the folder → Delete.

---

## 🛡️ 2. Set `ost-config.php` to Read-Only

To prevent changes to the configuration file:

- Navigate to `C:\inetpub\wwwroot\osTicket\include\ost-config.php`
- Right-click → Properties → Check **Read-only** → Apply

---

## 👥 3. Create and Customize User Roles

Go to **Admin Panel → Agents → Roles** and configure:

- Support Staff
- Managers
- Admins

Then assign roles to agents via **Admin Panel → Agents → Add New Agent**.

---

## 🛠️ 4. Configure Email Settings

### System Email:
- Go to **Admin Panel → Emails → Emails**
- Add your helpdesk email address (e.g., `support@yourdomain.com`)

### Fetching/Receiving Email:
- Enable IMAP/POP for your email
- Configure email fetching in osTicket for automatic ticket creation

---

## ✉️ 5. Enable Email Piping or Fetching

**POP/IMAP** is preferred for automatic ticket creation.

- Set up cron job using Windows Task Scheduler if using `cron.php`
- Command (adjust as needed):

```bash
php C:\inetpub\wwwroot\osTicket\cron.php
```

---

## 📂 6. Ticket Settings

Adjust ticket settings via:

- **Admin Panel → Settings → Tickets**
    - Auto-assign tickets
    - Require login for ticket status
    - Priority levels
    - SLA plans

---

## 📋 7. Help Topics and Departments

### Help Topics:
- Add common issue categories for users to select

### Departments:
- Set up different departments (e.g., IT Support, Billing)
- Route tickets to appropriate teams

---

## 🔧 8. System Logs and Monitoring

Check **Admin Panel → Dashboard → System Logs** to monitor issues.
Enable alerts for system-level warnings.

---

## 🧪 9. Test the System

- Submit test tickets via user portal
- Respond as staff
- Ensure email notifications are working
- Check ticket routing and permissions

---

## 🚀 10. Go Live!

Once fully configured:

- Share the user portal link: `http://<your-ip>/osTicket`
- Train your staff and start accepting real tickets.
