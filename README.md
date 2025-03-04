<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


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

- Create Virtual Machines and ensure both VM's are in the same Virtual Network/Subnet 
- Install Wireshark
- Ping Linux Vm to observe ICMP Traffic 
- Configuring a Firewall to deny incoming (inbound) ICMP traffic
- Observe SSH Traffic
- Observe DNS Traffic
- Observe RDP Traffic

<h2>Actions and Observations</h2>

<p>
<img width="640" alt="image" src="https://github.com/user-attachments/assets/1598bf17-d4f1-4e0f-a526-eb939d66394e" />
<img width="641" alt="image" src="https://github.com/user-attachments/assets/07a198a1-04bf-4d2b-82b2-058e6252cef8" />

</p>
<p>
After I created a Resource Group, and created both VM's. I wanted to verify that both Virtual Machines are in the same Virtual Network/Subnet.
</p>
<br />


<p>
<img width="863" alt="image" src="https://github.com/user-attachments/assets/310dcbc5-60a7-4e0d-aa1b-4ac7148865ac" />

</p>
<p>
Next, I installed WireShark and from Windows 10 Vm I pinged the Linux Vm using Powershell and the private IP address of the Ubuntu VM (Linux vm). Then I filtered the Wireshark to only observe ICMP traffic. Which will allow me to inspect it. 
</p>
<br />


<p>
<img width="900" alt="image" src="https://github.com/user-attachments/assets/23caaa61-a170-45e4-b15c-b15dd7f99033" />
<img width="943" alt="image" src="https://github.com/user-attachments/assets/5cadde05-63e8-4d6a-a3ac-4108a4dbe589" />

</p>
<p>
Then I initiated a perpetual/non-stop ping from the Windows 10 VM to my Ubuntu VM using Powershell. Within Azure, I Configured a Firewall in my Linux Vm [Network Security Group] to disable incoming (inbound) ICMP traffic. When I go back into WireShark you can see that request has been made, but my firewall is now blocking the traffic. ( ping private IP address -t)

</p>


<p>
<img width="776" alt="image" src="https://github.com/user-attachments/assets/2ae37963-2fb5-4d52-8a86-6e2ebf9c555f" />

</p>
<p>
In order, to observe SSH traffic we have to connect our user to Linux-Vm Private IP address using Powershell. ( ssh user@private IP address )


<p>
<img width="806" alt="image" src="https://github.com/user-attachments/assets/32aa062d-22af-4199-99df-36a48b38ac7e" />

</p>
<p>
In order, to observe DNS traffic we have to use Powershell. For my example, I used google.com (nslookup google.com)


<p>
 ![image](https://github.com/user-attachments/assets/36fcf624-ca17-4941-b5b2-81c73fa234e4)
 
</p>
<p>
Lastly, to observe RDP we type ( tcp.port == 3389 ) in WireShark to see RDP traffic. 
