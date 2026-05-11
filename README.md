<h1 align="center">Microsoft Azure: Configuring Active Directory</h1>

<hr>

<h2>Table Contents:</h2>

<ul>
  <li>Installing Windows Server</li>
  <li>Server Manager</li>
  <li>Active Directory and Services</li>
  <li>Promoting Domain Controller</li>
  <li>Microsoft Azure</li>
  
  
</ul>

<h2 align="center">Installing Windows Server</h2>


<div align="center">
  <table>
    <tr>
      <td valign="bottom">
        <img src="https://github.com/user-attachments/assets/ce2f1bba-bea3-427e-b20a-346d0b281932" width="620" height="300" alt="Step 1" /><br>
        <sub><b>Fig 1:</b> Initial Boot</sub>
      </td>
      <td valign="bottom">
        <img src="https://github.com/user-attachments/assets/357167cf-d567-4d83-bf7a-29823b914207" width="620" height="300" alt="Step 2" /><br>
        <sub><b>Fig 2:</b> OS Selection</sub>
      </td>
      <td valign="bottom">
        <img src="https://github.com/user-attachments/assets/1caf71c4-d8ed-4dc5-a293-58d8679d37c5" width="620" height="300" alt="Step 3" /><br>
        <sub><b>Fig 3:</b> Partitions</sub>
      </td>
    </tr>
  </table>
</div>



<p>
I create a virtual machine name Windows Server 2025 on Microsoft Azur platform where I go through configuring in networking and physical in virtual environment setting such as memory ram processor, iso file path file, size of gigabyte,number of cores, IP address, DHCP Server and DNS and Display setting. After creating the first virtual machine, the picture shows from above shows at the beginning of installation.I accept the agreement, select the Desktop Windows 2025, and create three different partitions. It took 2-3 minutes finishing installing Windows 2025 Desktop GUI.
Once it finishes installation, the virutal machine reboots and shows a administrator and password page.  
</p>


<h2 align="center">Creating two virtual machines on Microsoft Azure</h2>


<img width="1074" height="723" alt="image" src="https://github.com/user-attachments/assets/8b9ea316-ce2e-4690-94b3-f1e00f7f95c8" />

<p></p>

<br>

<h2>Server Manager </h2>

![Screenshot from 2025-02-10 23-24-41](https://github.com/user-attachments/assets/e75a5e14-e27b-47c0-a007-abd51b7c5fa9)

<p>
  The first step is I rename the computer name to HuskyTech-DC, so it will add in the Windows Active Directory: Users and Computers after setting up static IP address,
  DHCP server, and DNS server.
  
</p>

<br>

<h2>Installing Active Directory and other services</h2>

![Screenshot from 2025-02-10 23-31-53](https://github.com/user-attachments/assets/ac3b5dfc-ee40-48bb-9f6e-4c02fed8f909)

<p>
  The yellow icon when clicking for noftification is not showing a sign damage file just reminding to promote the domain controller, which I will deal later for the next one.
  In the picture, I went to Add to roles where all the services such as setting up Windows Deployment Service, Active Directory: Users and Computers, DHCP and DNS server, other componets.  

</p>

<br>

<img width="1599" height="853" alt="Screenshot from 2026-02-13 08-18-16" src="https://github.com/user-attachments/assets/5e4ecc11-76b5-411b-8850-528fcc9da42a" />
      <div align="center">
      <sub><b>Fig 4:</b> Server roles</sub>
      </div>  


<br>

<h2>Promoting domain controller</h2>

![Screenshot from 2025-02-10 23-32-38](https://github.com/user-attachments/assets/457c2928-8c7e-44d4-9b8e-e476659d973c)

<p>
  After setting up OrionWolfDC Domain, I go ahead promote and went through each steps and click start and restarting the computer once it checks its prequisities. 
  I selected add new forest radio button because I don't have other domain exist and I have to create new domain.
</p>

<br>

<img width="1024" height="741" alt="image" src="https://github.com/user-attachments/assets/5355c283-fcd0-424d-8b69-7fff09032837" />
 <div align="center">
      <sub><b>Fig 5:</b> Server roles</sub>
      </div>  
<p></p>

<h1 align="center">DHCP Server</h1>


<br>


<h2>Creating Scope</h2>


<img width="1389" height="760" alt="image" src="https://github.com/user-attachments/assets/cc79acca-10ab-433c-8b89-21c1978c9ea8" />


<p>
  After installing DHCP server, I open DHCP server and went to right click New Scope. I name Husky Scope and wrote in description said Range addreses from 172.168.22.100 - 172.168.22.200
</p>



<h2>IP Address Range</h2>

<img width="1361" height="718" alt="image" src="https://github.com/user-attachments/assets/5f423993-c8e9-4513-addf-35b956545a8b" />

<br>

 <p>I use the IP addresses I mention from Creating scope section and put 172.168.22.100 in Start Address and 172.168.22.200 in End.
 Lastly, I put subnet to 24 and it is equivalent as 255.255.255.0</p>



<h1>Add Exclusion addresses </h1>

<img width="1380" height="714" alt="image" src="https://github.com/user-attachments/assets/0962d643-9084-4e77-ba21-b79de6cedafb" />

<br>

<p>I add 172.168.22.102 from my Windows Server so it doesn't accidentally detect by DHCP server</p>


<h1>Configure DHCP Server Options</h1>

<br>

<p>I say yes configure DHCP server, so I won't go back configure manually myself </p>


<h2>Setting Router</h2>

<img width="1375" height="746" alt="image" src="https://github.com/user-attachments/assets/375ecae7-51e9-4312-8e6c-8fc6152f101a" />

<br>

<p> I skip this setp because I already setup in my Windows Server IP address setting already, so when I create another virtual machine and deploy with MDT.
It automatically picks up by DHCP server I setup.</p>


<h2>Activate Scope</h2>

<img width="1366" height="721" alt="image" src="https://github.com/user-attachments/assets/cd4918f6-204d-4522-a69d-ed19cec245d5" />


<p>And the last step I did is to activate the scope and it will complete wizard installation window box.</p>




<h2 align="center">Windows Remote Connection </h2>

<p>
  A Remote Connection in Windows allows users or administrators to access and control another Windows computer or server from a different location, as if they were sitting directly in front of it. This capability is essential for IT management, troubleshooting, remote work, and system administration in both enterprise and homelab environments.
</p>

<br>

<img width="1364" height="739" alt="image" src="https://github.com/user-attachments/assets/64794316-1008-46b4-981b-28c290e6609e" />

<br>

<p>
  This image shows a Remote Desktop connection being made to a Windows computer in my HuskyTech homelab. The Remote Desktop feature is turned on in Windows Settings, which allows the system to accept connections from other devices on the same network or domain. In the Remote Desktop Connection window, the user is connecting to DESKTOP-0TRL91E.HuskyTech.local using the domain account HUSKYTECH\Helpdesk.

This setup lets me manage and control my virtual machines from one workstation instead of logging into each one directly. It’s a great way to simulate how IT administrators handle remote access in real business environments—perfect for testing Active Directory authentication, performing system updates, or troubleshooting client machines inside my homelab network.
</p>


<img width="972" height="598" alt="image" src="https://github.com/user-attachments/assets/8817b965-b02a-470d-9024-05ab214772de" />

<br>

<p>
I am connecting to DESKTOP-0TRL91E.HuskyTech.local using the HUSKYTECH\Helpdesk domain account. At this stage, Windows asks for the account password to verify credentials before granting access.

This step is part of establishing a secure remote session through Remote Desktop Protocol (RDP). It’s a common process in IT environments, where administrators or support technicians remotely log in to servers or client machines for troubleshooting, software updates, and general system management.
</p>


<br>

<img width="810" height="602" alt="image" src="https://github.com/user-attachments/assets/ab2ee3f7-aec8-46f9-8e82-19da963945e0" />

<br>


<p>As the Domain Controller is connecting to the other virutal machine, the other virtual machine will logout.</p>

<br>

<img width="1361" height="702" alt="image" src="https://github.com/user-attachments/assets/50966a27-859d-4781-b97a-f4fbdf229f83" />
<br>
<hr>

<p>
After successfully entering the credentials, the Remote Desktop session connects to the target computer DESKTOP-0TRL91E.HuskyTech.local. The desktop background displays the custom HuskyTech logo, confirming that the connection to the domain environment was established successfully.

This final screen demonstrates a completed remote session inside the HuskyTech homelab, showing that Remote Desktop Protocol (RDP) is fully functional across the network. From here, the user can manage applications, perform administrative tasks, or test remote access tools like RustDesk and Microsoft Edge.

Overall, this setup highlights how Remote Desktop can be used to simulate real-world IT environments—allowing administrators to securely connect, configure, and control systems within a virtual lab network.
  
</p>




