<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create virtual machines in Azure
- Connect to Windows VM
- Install and use wireshark
- Test Network Communication

<h2>Actions and Observations</h2>

---

Here’s a simple explanation of each major step, written at an 11th-grade level:  

### **Part 1: Creating Virtual Machines in Azure**  
**Purpose:** Set up two virtual machines (VMs) in the cloud so we can later observe how they communicate with each other.  

1. **Create a Resource Group**  
   - A resource group is like a folder that keeps all related resources together in Azure.  
   - This helps organize and manage everything easily.  

2. **Create a Windows 10 Virtual Machine (VM)**  
   - A virtual machine is a computer that runs in the cloud instead of on your desk.  
   - While setting it up, we tell Azure to place it in the resource group we just created.  
   - It also creates a new virtual network (VNet) so that devices in this network can talk to each other.  

3. **Create a Linux (Ubuntu) VM**  
   - We add another computer, this time using Linux (Ubuntu), which is a different operating system from Windows.  
   - It must be placed in the same resource group and virtual network as the Windows VM.  
   - This setup allows the two VMs to communicate later in Part 2.  

4. **Confirm Both VMs Are in the Same Virtual Network**  
   - This ensures the two VMs can "see" each other when we test communication.  

---

### **Part 2: Observing ICMP Traffic**  
**Purpose:** Use networking tools to watch data travel between the two virtual machines.  

1. **Connect to the Windows 10 VM via Remote Desktop**  
   - Remote Desktop lets us control the Windows VM from our own computer.  
   - If using a Mac, we need to install Microsoft Remote Desktop to connect.  

2. **Install Wireshark on the Windows VM**  
   - Wireshark is a tool that captures and shows network traffic.  
   - It helps us see what happens when computers send messages to each other.  

3. **Filter for ICMP Traffic in Wireshark**  
   - ICMP (Internet Control Message Protocol) is the type of traffic used for **ping** commands.  
   - Filtering for ICMP in Wireshark allows us to focus on just those messages.  

4. **Ping the Linux VM from the Windows VM**  
   - We find the Linux VM's private IP address and use a **ping** command from the Windows VM.  
   - In Wireshark, we can observe the request being sent and the reply coming back.  
   - This confirms that the two VMs are communicating over the network.  

This lab helps understand cloud networking, virtual machines, and how computers talk to each other over a network.
