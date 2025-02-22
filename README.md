<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Dealing with account lockouts
- Configuring Group Policy for Account Lockout
- Enabling and Disabling Accounts
- Observing Logs

<h2>Actions and Observations</h2>

---

### **1. Dealing with Account Lockouts**  
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
What it does: This step simulates a scenario where a user enters the wrong password multiple times, leading to an account lockout.  

**Purpose:** Organizations enforce account lockouts to protect against unauthorized access and brute-force attacks. By testing this, administrators can understand how lockouts work and how to resolve them.  

**Steps:**  
- **Log into DC-1 (Domain Controller).**  
- **Pick a random user account created previously.**  
- **Attempt to log in 10 times with a bad password.**  
  - This simulates a user forgetting their password or an attacker trying to guess it.  

---

### 2. Configuring Group Policy for Account Lockout 
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
What it does: This step modifies security settings so that an account locks out after five incorrect login attempts instead of the default settings.  

**Purpose:** Setting a limit on failed login attempts helps prevent brute-force attacks while maintaining security for legitimate users.  

**Steps:**  
- **Configure the "Account Lockout Threshold" policy in Group Policy to lock accounts after five failed attempts.**  
- **Attempt to log in six times with a bad password.**  
  - The account should now be locked due to the new policy.  
- **Observe that the account is locked in Active Directory.**  
  - This confirms that the policy is working as expected.  
- **Unlock the account and reset the password.**  
  - This step ensures that an administrator can restore access when needed.  
- **Attempt to log in with the new password.**  
  - Verifies that the account is functioning again.  

---

### **3. Enabling and Disabling Accounts**  
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
What it does: This step demonstrates how administrators can disable and re-enable user accounts in Active Directory.  

**Purpose:** Disabling accounts is useful when employees leave the company or need temporary access restrictions without deleting their accounts.  

**Steps:**  
- **Disable the same user account in Active Directory.**  
- **Attempt to log in with it and observe the error message.**  
  - Confirms that disabled accounts cannot be accessed.  
- **Re-enable the account in Active Directory.**  
- **Attempt to log in again.**  
  - Verifies that the account is now active and accessible.  

---

### **4. Observing Logs**  
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
What it does: This step involves checking system logs on both the Domain Controller and the client machine to track authentication events.  

**Purpose:** Logs help administrators monitor failed login attempts, security threats, and troubleshooting issues related to user authentication.  

**Steps:**  
- **Observe the security logs in the Domain Controller.**  
  - This shows details about failed login attempts, account lockouts, and password resets.  
- **Observe the logs on the client machine.**  
  - Helps verify if the client machine properly logged authentication events.  

---

Arrange in the correct order (clean up)
Client1
![image](https://github.com/user-attachments/assets/7c5b592c-ffa8-446c-82f6-4fa76962e9e9)
![image](https://github.com/user-attachments/assets/a7e6f10f-a7c0-437c-a9ac-5b00a84d48af)
Create Users
![image](https://github.com/user-attachments/assets/736f60ab-6be7-4d6c-bdd6-0e00e2e6f095)
Checking user login created in active directory
![image](https://github.com/user-attachments/assets/6e4aaa33-5499-41dd-8d83-8fdb010eb030)

Observe that the account has been locked out within Active Directory
![image](https://github.com/user-attachments/assets/cc0a4d82-0924-4771-b185-99eb41bc6498)

Unlock the account
![image](https://github.com/user-attachments/assets/a349fceb-3829-4042-8184-b8b5df3dc379)

Reset Password
![image](https://github.com/user-attachments/assets/bf732a9f-9478-4eb0-9ca2-b3561ac675a2)




