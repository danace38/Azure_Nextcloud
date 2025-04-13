## ☁️ Nextcloud in Azure

This project showcases the deployment of a Nextcloud web server using a Virtual Machine in Microsoft Azure. 

## 📖 Table of Contents
- [Overview](#overview)
- [Architecture](#architecture)
- [Technologies Used](#technologies-used)
- [Setup & Deployment](#technologies-used)


## 🔍 Overview

I created this project as part of my journey to build practical cloud engineering skills - with a focus on undestanding core concepts in **networking** and **security** within the Azure ecosystem. 

Furthemore, it has been a long-time goal of mine to set up a self-hosted platform where I have full control over my data. I've always been interested in learning how to host and manage my own services rather than relying solely on third-party platforms (e.g., Google Drive, iCloud, OneDrive, etc)

## 🏗️ Architecture

This project uses several core Azure components to build a secure and functional environment for hosting a self-managed Nextcloud server:

* **Resource Group** - A container that holds all resources related to the project.
* **Virtual Machine (VM)** - Hosts the Nextcloud web server.
* **Network Interface Controller (NIC)** - Connects the VM to the subnet and virtual network; exposes the public IP.
* **Virtual Network (VNET)** - Provides a private network environment for the VM.
* **Subnet** - A logical segment of the VNET where the VM is deployed.
* **Network Security Group (NSG)** - Controls inbound and outbound traffic to the subnet and VM using custom rules.
* **Azure Bastion** - Enables secure SSH access to the VM via the Azure portal without exposing it to the public internet.
* **Public IP and DNS Label** - Used to make the Nextcloud server publicly accessible via a custom domain name.

###  **Diagram (Architecture Overview)**
![Architecture Diagram](Azure_NextCloud_Diagram1.png)

# 🧰 Technologies Used
* **Microsoft Azure** - Cloud platform for deploying and managing infrastructure
* **Nextcloud** - Self-hosted, open-source web server for file storage
* **Ubuntu Linux (22.04)** - OS running on the VM
* **Azure Bastion** - Secure SSH access to the VM
* **Azure Virtual Network (VNET)** - Provides the private network environment
* **Network Security Group (NSG)** - Defining and applying traffic control rules


# 🚀 Setup & Deployment
This project was deployed through the **Azure Portal**, while the Nextcloud server was installed and configured using the command line interface (CLI) directly on the virtual machine.

### Key steps of the project

1. Creating **Resource Group** for all resources related to this project
![Resource Group](Azure_NextCloud_ResourceGroup.png)

2. Creating **VNET** and **Subnet** for network isolation inside the resource group
![VNET](Azure_NextCloud_VNET.png)

3. Creating **NSG** around the subnet to allow/deny inbound and onbound traffic
![NSG](Azure_Nextcloud_NSG.png)

4. Deploying **Bastion** to connect to a VM
![Bastion](Azure_Nextcloud_Bastion.png)

5. Creating an **Ubuntu Server VM**
![VM](Azure_Nextcloud_VM.png)

6. Connect to VM using **Bastion via SSH**
![SSH](Azure_Nextcloud_SSH.png)

Once connected to VM, the following CLI commands are required to set up Nextcloud:

* Install Nextcloud packages

``
sudo snap install nextcloud
``

* Set up admin account

``
sudo nextcloud.manual-install admin password
``

* Create self-signed certificate

``
sudo nextcloud.enable-https self-signed
``

