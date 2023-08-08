<h1>Streamlining PC Deployments with Windows Deployment Services: A Step-by-Step Guide for IT Technicians</h1>
<hr></hr>
<p>In this guide, we will be exploring how to customize installs across multiple machines over the network.</p>

<h2>Environments and Technologies Used:</h2>
<ul>
  <li>Microsoft Azure</li>
  <li>Windows Server w/ Windows Deployment Services</li>
  <li>Remote Desktop</li>
</ul>

<h2>Operating Systems Used:</h2>
<hr></hr>
<ul>
  <li>Windows Server 2022</li>
  <li>Windows Server 2019 Evaluation</li>
  <li>Windows 10</li>
</ul>

<h2>Description:</h2>
<p>Efficiently installing and deploying Windows across multiple PCs is a crucial task for IT technicians and system administrators. Windows Deployment Services (WDS) is a powerful tool that simplifies this process by enabling the capture, customization, and deployment of Windows image files. In this project, we will explore how to set up and utilize WDS for seamless mass deployments, ensuring consistent configurations across all installations.</p>

<b>Understanding Windows Image Files:</b>
<p>At its core, a Windows image file is a snapshot of a Windows installation that encapsulates all the software, group policy configurations, and registry edits tailored to your specific needs. These image files also ensure that any identifying information from the original PC is meticulously stripped out, enabling you to install the customized version of Windows onto another PC seamlessly, as if it were a brand-new installation.</p>
<b>Deploying Windows Over the Network:</b>
<p>With Windows Deployment Services, deploying Windows to a new PC over the network becomes a breeze. It empowers IT technicians to install the desired version of Windows along with all the additional software and custom driver packages for the hardware. The ability to maintain a consistent configuration across multiple installations becomes particularly invaluable during mass deployments, ensuring a standardized and efficient environment.</p>
<b>Project Scope:</b>
<p>In this project, our primary focus will be on setting up WDS, configuring its essential components, and exploring its key functionalities. We will cover three fundamental aspects:</p>
  <ol>
  <li>Installing the Service: We will guide you through the step-by-step process of installing Windows     Deployment Services on your Windows Server. By the end of this phase, you will have a fully functional WDS environment ready to revolutionize your deployment strategy.</li>
  <li>Adding Boot Install Images: Delve into the world of boot install images, essential for initiating network-based installations. We will demonstrate how to add and manage these images, ensuring a seamless boot-up experience for your clients.</li>
  <li>Booting Clients Over the Network: Finally, we will empower you to configure your client systems to boot over the network, unlocking the full potential of WDS for your deployment operations.</li>
  </ol>
<p>By the end of this project, you will possess a comprehensive understanding of Windows Deployment Services, allowing you to optimize your deployment workflows, increase efficiency, and standardize your network configurations.</p>
<hr></hr>

<h3>Step 1: Obtain a Windows Server</h3>
<p>To get started with Windows Deployment Services (WDS), you'll need a Windows Server environment. You can either set up a Windows Server 2019 Virtual Machine on Microsoft Azure or download Windows Server directly from the Microsoft website for your home or work machine. Ensure you have the required administrative access and network connectivity before proceeding with the WDS setup. Let's move on to the next steps to configure and utilize WDS for seamless PC deployments.</p>
<img width="800" height="500" alt="Spinning up Windows Server in Azure" src="https://github.com/SamEshaia/Windows-Deployment-Services/assets/124312452/10b7bfca-9152-43b7-8020-827176eafe26"/>

<h3>Step 2: Install Windows Deployment Services</h3>
<ul>
  <li>Open Server Manager from the start menu</li>
  <li>Click "Manage" in the top right corner and select "Add Roles and Features."</li>
  <li>Proceed through the first three sections by clicking "Next."</li>
  <li>In the Server Selection section, scroll down and check the box for "Windows Deployment Services."</li>
  <li>A few dependencies will appear; click the "Add Features" button.</li>
  <li>Click "Next" two more times until you reach the Role Services section under WDS.</li>
  <li>Ensure that "Deployment Server" and "Transport Server" are checked, and then click "Next."</li>
  <li>•	Make sure the install looks like the image below and click Install. Then when the install is finished click closed.</li>
</ul>
<img width="800" height="500" alt="Screenshot 2023-08-07 at 8 42 48 PM" src="https://github.com/SamEshaia/Windows-Deployment-Services/assets/124312452/e40f87ae-fe50-4988-a54e-4e243e522c50"/>

<h3>Step 3: Open Windows Deployment Services</h3>
<p>Next, we are going to open Windows Deployment Services by typing it into the start menu search bar. Feel free to pin that application to the start menu and the task bar for easier access later. Go ahead and open Windows Deployment Services. Once the window pops up, click on the drop-down arrow next to “Servers” and you will see a server icon with a warning sign on it. Don’t worry that just means we have to configure our server first.</p>
<img width="800" height="500" alt="Step 3" src="https://github.com/SamEshaia/Windows-Deployment-Services/assets/124312452/22af60e1-e7b9-4d09-ab3d-9b218cb2a773"/>
<h3>Step 4: Configure your Server</h3>
<p>Next, right click on the server in the drop down menu under “Servers” and click “Configure Server”. A window will pop up warning you of the pre-requisites for having a server. 
Before you move ahead please keep in mind all the requirements listed below are met:</p>
<ul>
  <li>•	Be a member of an Active Directory Domain (we are doing a standalone install so no need to worry about that).</li>
  <li>Have an active DHCP Server and active DNS Server (Pretty much every network you are going to work on qualifies for this).</li>
  <li>The server has an NTFS file system partition on which to store images (we also qualify for this as well).</li>
</ul>
<p>If that all looks good, go ahead and click on “Next”.</p>
<img width="800" height="500" alt="Step 4a" src="https://github.com/SamEshaia/Windows-Deployment-Services/assets/124312452/ddf3f670-4ad8-476d-92f6-dcbaf692f1e4"/>
<p>After the pre-requisites, you will have to choose between “Integrated with Active Directory” or “Standalone server”. The installation feature is pretty much identical and, in this case, because it’s a home lab, we are going to do a standalone install. Click Next once you have chosen “Standalone server”.</p>
<img width="800" height="500" alt="Step 4b" src="https://github.com/SamEshaia/Windows-Deployment-Services/assets/124312452/7687dc83-2c2e-4e51-a8b4-d53e00c45093" />
<p>After you have chosen an install option, it will prompt you to choose a file location. This is where windows deployment services stores all of the windows images that it will be deploying out to clients. By default, it creates a path to the C:\ drive. If you are installing on to network storage, you will want to define that here. For our use case, we are just going to use the default C:\ drive so go ahead and click “Next.”</p>
<img width="800" height="500" alt="Step 4c" src="https://github.com/SamEshaia/Windows-Deployment-Services/assets/124312452/6c9ddbb9-324b-43e3-b53c-d997350cc8aa"/>
<p>After that, a warning will pop up if you ware installing onto the C:\ drive but because this is a home lab environment, we are okay. So, go ahead and click “Yes”.</p>
<img width="800" height="500" alt="Step 4d" src="https://github.com/SamEshaia/Windows-Deployment-Services/assets/124312452/44718fab-3eb4-4939-accf-2283dd68c23b"/>
<p>Next under PXE server settings, we are going to select “Respond to all clients computers (known and unknown)”. This will unlock Windows Deployment Services to allow any client on your Network to net boot in and get windows installed. After this click on “Next”.</p>
<img width="800" height="500" alt="Step 4e" src="https://github.com/SamEshaia/Windows-Deployment-Services/assets/124312452/b022c000-3b47-4b35-929e-834fd8912287"/>
<p>After the install operation is complete, WDS is officially up and running but you will have one final window asking you to “Add images to the server now”. Make sure to uncheck that box and we will come back to that later. For now, click on “Finish”.</p>
<img width="800" height="500" alt="Step 4f" src="https://github.com/SamEshaia/Windows-Deployment-Services/assets/124312452/52139e1f-cd9d-4e87-9614-f98f30d13df7"/>
<p>Once WDS is installed and running, you should be able to click the drop-down menu arrow next to your server and see a number of folders drop down. The ones we are going to be interested in during the next steps are the “Install Images” and “Boot Images”.</p>
<img width="800" height="500" alt="Step 4f" src=https://github.com/SamEshaia/Windows-Deployment-Services/assets/124312452/af6d1d88-0f67-42ce-b811-a83c0cd083ce" />
<h3>Step 5: Acquire the ISO file for Windows Server 2019 or 2022 Evaluation and Windows 10 (Home or Pro)</h3>
<p>For this guide, you will need to acquire the ISO file for Windows Server 2019 or 2022 Evaluation and Windows 10. You can acquire these from Microsoft’s Website or to make it easy, I have provided them in a zip file which you can download: <a href="https://drive.google.com/file/d/1-j_OHnORe-c82FvqJEoEDpGFD-aTVZh7/view?usp=drive_link
">https://drive.google.com/file/d/1-j_OHnORe-c82FvqJEoEDpGFD-aTVZh7/view?usp=drive_link</a></p>
<img width="800" height="500" alt="Step 4f" src="https://github.com/SamEshaia/Windows-Deployment-Services/assets/124312452/94eaeef3-8770-4fc9-b557-5da30deb3e4e"/>
