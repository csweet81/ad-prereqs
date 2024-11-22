<p align="center">
<img src="https://i.imgur.com/pJSsvpx.png" alt=""/>
</p>

<h1>Active Directory - Installation & Configuring</h1>
<p>
This tutorial demonstrates how to test network configurations, geo-restrictions, and VPN functionality using Azure Virtual Machines and ProtonVPN. By creating a virtual machine in one location and connecting it to a VPN in another, we explore how public IPs change, regional content variations, and VPN privacy impact user experiences.<br />

In summary, this walkthrough provides a practical framework for testing content localization, ensuring compliance, and evaluating VPN security, offering valuable insights for IT teams, developers, and cybersecurity professionals. 
</p>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
- ProtonVPN

<h2>Operating Systems Used</h2>

- Windows 10</b> (21H2)

<h2>List of Steps</h2>

- Step 1: Create a Resource Group
- Step 2: Create a Virtual Network and Subnet
- Step 3: 

<h2>Installation Steps</h2>

<h3>Setup Domain Controller in Azure</h3>

<img src="https://i.imgur.com/LXakI0h.png" height="80%" width="80%" alt=""/>

- Action: Open a web browser on your actual computer (not a virtual machine) and go to https://whatismyipaddress.com/.
- Purpose: This shows your public IP address as assigned by your Internet Service Provider.
- Result: Copy the IP address shown on the page and save it in a text file (e.g., MyIP.txt) for reference.

<h3>Step 2: Create a Resource Group in Azure</h3>

<img src="https://i.imgur.com/ENjW05T.png" height="80%" width="80%" alt=""/>

- Action: Log into your Azure Portal at https://portal.azure.com.
- Navigate: Click on Resource Groups from the navigation menu on the left-hand side.
- Create Resource Group:
  - Click + Create or Add.
  - Enter a name for the resource group (e.g., "TestVMGroup").
  - Select a region for the resource group. (This can be your current location.)
  - Click Review + Create and then Create.

<h3>Step 3: Create a Windows 10 Virtual Machine</h3>

<img src="https://i.imgur.com/A4W0wBB.png" height="80%" width="80%" alt=""/>

- Navigate: In the Azure Portal, search for Virtual Machines in the top search bar and select it.
- Create VM:
  - Click + Create and choose Azure Virtual Machine.
  - Under Basics, fill out the details:
    - Select the previously created Resource Group.
    - Give the VM a name (e.g., "TestVM").
    - Choose an image: Windows 10 Pro or Enterprise.
    - Select a region in a different country (e.g., Europe or Asia).
    - Choose a size (e.g., Standard D2s_v3 for light use).
    - Set admin username and password for login.
- Click Review + Create, then Create.
- Wait for Deployment: Once deployment completes, navigate to the VM's Overview page.

<h3>Step 4: Log Into the VM Using Remote Desktop</h3>

<img src="https://i.imgur.com/ysfJ0QP.png" height="80%" width="80%" alt=""/>

- Download RDP File:
  - On the VM's Overview page, click Connect > RDP.
  - Download the .rdp file.
- Open Remote Desktop:
  - Open the downloaded .rdp file.
  - Enter the admin username and password set during VM creation.
- Log In: Connect to the virtual machine’s desktop.

<h3>Step 5: Check the VM’s IP Address</h3>

<img src="https://i.imgur.com/jHokyQi.png" height="80%" width="80%" alt=""/>

- Action: Open a browser within the VM and go to https://whatismyipaddress.com/.
- Result: Note the new IP address displayed, which will reflect the VM’s geographic location.
- Save: Copy this IP address and save it in the text file for comparison.

<h3>Step 6: Sign Up for ProtonVPN</h3>

<img src="https://i.imgur.com/1lJMaD6.png" height="80%" width="80%" alt=""/>

- Action: On your actual computer, sign up for a free ProtonVPN account at https://account.protonvpn.com/signup?plan=free&language=en.
- Complete Registration: Follow the steps to create an account (you may need to verify your email).
- Save Credentials: Note down the username and password for use later.

<h3>Step 7: Install ProtonVPN on the VM</h3>

<img src="https://i.imgur.com/DvPJrfh.png" height="80%" width="80%" alt=""/>

- Action: On the VM, download the ProtonVPN client from https://protonvpn.com/.
- Install: Follow the installation process within the VM.
- Login: Log in with the ProtonVPN account credentials created earlier.

<h3>Step 8: Connect to a VPN Server</h3>

<img src="https://i.imgur.com/Q2AO7JN.png" height="80%" width="80%" alt=""/>

- Action: In the ProtonVPN client, choose a VPN server in a different country (e.g., Japan or another far location).
- Connect: Wait for the VPN to establish a secure connection.

<h3>Step 9: Check the VPN’s IP Address</h3>

<img src="https://i.imgur.com/IxZBzyC.png" height="80%" width="80%" alt=""/>

- Action: Open a browser within the VM (while connected to the VPN) and go to https://whatismyipaddress.com/.
- Result: Note the new IP address, reflecting the VPN server’s geographic location.
- Save: Record this new IP address in the text file.

<h3>Step 10: Test Websites with the VPN</h3>

- Browse to Test Sites: While still on the VM and connected to the VPN, visit websites like:
  - Google
  - Disney
  - Amazon
- Observe Changes:
  - Does Google display results in a different language or domain (e.g., .jp for Japan)?
  - Does Disney redirect to a localized page?
  - Does Amazon show local prices, offers, or products for the VPN server’s location?
- Document Observations: Note any changes in site behavior or presentation and save these observations.
