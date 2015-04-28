# Create a Virtual Machine from an Image

<a href="https://azuredeploy.net/" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

This template uses the Azure Linux OSPatching extension to deploy an Linux VM. Azure Linux OSPatching extension enables the Azure VM administrators to automate the VM OS updates with the customized configurations.

You can use the OSPatching extension to configure OS updates for your virtual machines, including:

1. Specify how often and when to install OS patches
2. Specify what patches to install
3. Configure the reboot behavior after updates

Below are the parameters that the template expects

| Name   | Description    |
|:--- |:---|
| newStorageAccountName  | Unique DNS Name for the Storage Account where the Virtual Machine's disks will be placed. |
| adminUsername  | Username for the Virtual Machines  |
| adminPassword  | Password for the Virtual Machine  |
| dnsNameForPublicIP  | Unique DNS Name for the Public IP used to access the Virtual Machine. |
| subscriptionId  | Subscription ID where the template will be deployed |
| vmSourceImageName  | Source Image Name for the VM. Example: b39f27a8b8c64d52b05eac6a62ebad85__Ubuntu-14_04_2_LTS-amd64-server-20150309-en-us-30GB |
| location | location where the resources will be deployed |
| virtualNetworkName | Name of Virtual Network |
| vmSize | Size of the Virtual Machine |
| vmName | Name of Virtual Machine |
| publicIPAddressName | Name of Public IP Address Name |
| nicName | Name of Network Interface |
| rebootAfterPatch | The reboot behavior after patching |
| dayOfWeek | The patching date (of the week)You can specify multiple days in a week. |
| startTime | Start time of patching |
| category" | Type of patches to install |

}
