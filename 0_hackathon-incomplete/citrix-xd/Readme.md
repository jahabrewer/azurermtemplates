# ARM Templates for Citrix XenApp and XenDesktop

This template creates a new AD Forest and a XenDesktop Controller (DDC) with a site configured, as well as a configurable number of Machine Catalogs. Each Machine Catalog is a set of VMs with the Citrix VDA installed and configured to use to the XenDesktop Controller. At this point, this template only creates the Machine Catalog VMs; it does not create Machine Catalog objects in XenDesktop.

Click the button below to deploy

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fjahabrewer%2Fazurermtemplates%2Fmaster%2F0_hackathon-incomplete%2Fcitrix-xd%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

## How to use

The defaults for parameters work fairly well where they're provided. The parameter you'll want help with is `xdMediaUri`. It should be the URI of a ZIP file of XenDesktop 7.5 (other versions may work, only tested with 7.5) installation media. The ZIP file should have the same directory structure as the installation media ISO. The first level directories should include `Documentation`, `Support`, `x64`, and `x86` among others.

# Todo items

- [ ] Create a SQL Server VM and modify the XenDesktop Site setup DSC to use it instead of the local SQL Express instance
- [ ] Get the Machine Catalog template to register the VMs it creates as a Machine Catalog in XenDesktop
- [ ] Add support for multiple storage accounts in the Machine Catalog template
- [ ] Figure out if it's possible to use the AD Load Balancer for all RDP access instead of creating a Public IP for the DDC
- [ ] Automate licensing to use a trial or uploaded license file

# Help

File a github issue or email me directly (janzen.brewer@citrix.com).

# Known Issues

It's not clear where the problem lies, but there is a moderate rate of both spurious and actual failures when the DSC extension runs. The primary template doesn't suffer from this problem as much as the Machine Catalog template. The spurious failures tend to have error messages relating to not being able to lock a file (because an old DSC instance is running). The actual failures tend to have error messages saying that the DSC extension was not installed correctly.

# Contributors

These templates were born at a Microsoft hackathon attended by:

* Janzen Brewer (@jahabrewer)
* Alex Stoddard (@alexstoddard)
* Ashok Rajan
* Prasanna Padmanabhan

The DSC modules used are derivatives of modules created by Citrites **Brian Ehlert** (`Citrix\_XenDesktopRole`, [blog entry](http://blogs.citrix.com/2014/10/07/desired-state-configuration-xendesktop-dsc-resource-and-azure-dsc-vm-extension-part-6/)) and **Kirk MacPhee** (`Citrix\_XenDesktopDatabase`, `Citrix\_XenDesktopSite`).

Internally, the template uses @simongdavies's [active-directory-new-domain template](https://github.com/Azure/azure-quickstart-templates/tree/master/active-directory-new-domain) to create an AD Forest and Domain Controller.
