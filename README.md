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
  <li>Make sure the install looks like the image below and click close.</li>
</ul>
<img width="800" height="500" alt="Screenshot 2023-08-07 at 8 42 48 PM" src="https://github.com/SamEshaia/Windows-Deployment-Services/assets/124312452/e40f87ae-fe50-4988-a54e-4e243e522c50"/>
