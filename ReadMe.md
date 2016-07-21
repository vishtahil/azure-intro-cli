# Azure Intro Commands

**Use the following command to enable the Azure Resource Manager commands:**

* *azure config mode arm*

### **Command for refistering the provider**
* **azure provider register Microsoft.Compute** 

### **Connect to Your Azure Subscription**

1. Open a browser and navigate to <https://aka.ms/devicelogin>. The command prompt will display a device code that you can use to authenticate to Azure.

2. Once you enter the code, you will be prompted to allow access to the Microsoft Azure CLI. Click Continue.

#### **Create Resource Group**

* *azure group create –n “CLITestGroup” –l “West US”*

#### **Create a Virtual Network**

* *azure network vnet create –g "CLITestGroup" –n “TestVNET” -l "West US"*

#### **Create a Subnet**

* *azure network vnet subnet create -g "CLITestGroup" --vnet-name "TestVNET" -n "TestSubnet" --address-prefix 10.0.1.0/24*

#### **Create a public address**

* *azure network public-ip create -g "CLITestGroup" -n "TestPIP" -l "West US" –-allocation-method “Dynamic”*

#### **Assign Domain Name Label to Public Address. Domain name label to be unique**

* *azure network public-ip set -g "CLITestGroup" -n "TestPIP" --domain-name-label "demoexample"*

#### **Create Network Interface Card**

* *azure network nic create -g "CLITestGroup" -l "West US" -n "TestNIC" --subnet-name "TestSubnet" --subnet-vnet-name "TestVNET" --public-ip-name “TestPIP”*

#### **Create Virtual Machine**

1. *azure vm image list-publishers -l "West US"*
2. *azure vm image list-offers -l "West US" -p "MicrosoftWindowsServer"*
3. *azure vm image list-skus -l "West US" -p "MicrosoftWindowsServer" -o "WindowsServer"*
4. *azure vm image list -l "West US" -p "MicrosoftWindowsServer" -o "WindowsServer" -k "2012-R2-Datacenter"*
5. *azure vm create -g "CLITestGroup" -n "TestVM" -l "West US" --nic-name "TestNIC" --os-type "Windows" --image-urn MicrosoftWindowsServer:WindowsServer:2012-R2-Datacenter:4.0.20151214 --admin-username "Attendee" --admin-password "#1AzurePro$"*
6. **RDP to Virtual Machine**

#### **Delete Resource Group**
azure group delete –n “CLITestGroup”

[**Reference Link**](https://courses.edx.org/courses/course-v1:Microsoft+DEV205Bx+2T2016/courseware/6d965d92c27341f49f68ddf9cb0110e2/2008f2f2d3954c1ea21c807b133c4be5/)