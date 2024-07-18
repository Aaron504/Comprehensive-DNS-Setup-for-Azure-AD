

<h1>Comprehensive DNS Setup for Azure AD</h1>
This repository contains detailed instructions and resources for setting up and managing DNS in a hybrid Active Directory environment integrating on-premises infrastructure with Azure Cloud. The lab focuses on understanding DNS configurations, ensuring seamless connectivity and name resolution across both environments.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Contents:</h2>

- Overview of DNS in Active Directory
- Configuring DNS for on-premises AD
- Integrating DNS with Azure AD
- Testing and verifying DNS resolution
- Troubleshooting common DNS issues

<h2>High Level Configuration Steps</h2>

- A-Record Exercise
- Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)
- Connect/log into Client-1 as an admin (mydomain\jane_admin)
- From Client-1 try to ping “mainframe” notice that it fails
- Nslookup “mainframe” notice that it fails (no DNS record)
- Create a DNS A-record on DC-1 for “mainframe” and have it point to DC-1’s Private IP address
- Go back to Client-1 and try to ping it. Observe that it works
![Screenshot 2024-07-18 170450](https://github.com/user-attachments/assets/23a1568d-5183-4327-927b-ee3271ec2878)
![Screenshot 2024-07-18 170702](https://github.com/user-attachments/assets/92ed85fa-7b5f-4d7b-9617-d05d864938a2)
![Screenshot 2024-07-18 171023](https://github.com/user-attachments/assets/1a8ea71f-5162-44f0-96ac-e24b563e3b56)
![Screenshot 2024-07-18 171942](https://github.com/user-attachments/assets/455b26fd-4aed-4a8a-94c0-7fec5467f5de)
![Screenshot 2024-07-18 172220](https://github.com/user-attachments/assets/6d948680-9f4c-4eff-a0d7-9f5a2b81cf53)
![Screenshot 2024-07-18 172443](https://github.com/user-attachments/assets/bdc8a710-ed95-4f48-8ec4-54c70d669d44)

- Local DNS Cache Exercise
- Go back to DC-1 and change mainframe’s record address to 8.8.8.8
- Go back to Client-1 and ping “mainframe” again. Observe that it still pings the old address
- Observe the local dns cache (ipconfig /displaydns)
- Flush the DNS cache (ipconfig /flushdns). Observe that the cache is empty
- Attempt to ping “mainframe” again. Observe the address of the new record is showing up
![Screenshot 2024-07-18 173155](https://github.com/user-attachments/assets/0f466867-6945-4c6e-b8c7-5ccab0c1eff3)
![Screenshot 2024-07-18 173430](https://github.com/user-attachments/assets/b46bc918-14d8-499c-8661-757c26459e2e)
![Screenshot 2024-07-18 173554](https://github.com/user-attachments/assets/a8191351-c572-4c30-a148-84499cc76e2f)
![Screenshot 2024-07-18 173902](https://github.com/user-attachments/assets/f42af17f-ccd0-454b-8166-7ebc5a19908c)
![Screenshot 2024-07-18 174037](https://github.com/user-attachments/assets/ab614a34-da8a-427d-941a-642add3f8f45)

- CNAME Record Exercise
- Go back to DC-1 and create a CNAME record that points the host “search” to “www.google.com”
- Go back to Client-1 and attempt to ping “search”, observe the results of the CNAME record
- On Client-1, nslookup “search”, observe the results of the CNAME record
![Screenshot 2024-07-18 174545](https://github.com/user-attachments/assets/a34a6d33-a3cb-4322-a6a8-19b263b8fc42)
![Screenshot 2024-07-18 174724](https://github.com/user-attachments/assets/039b6e1c-6683-4ca2-881e-e1854696529d)
![Screenshot 2024-07-18 175131](https://github.com/user-attachments/assets/d0e2012e-f029-41ef-982f-0c59b18bb31f)



















