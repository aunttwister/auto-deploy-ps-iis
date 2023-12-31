# **Auto redeploy Angular & .NET to IIS with PowerShell**

This selection of scripts utilizes PowerShell to deploy your Angular and .NET apps to IIS. This is still a work in progress as it can be either made simpler or can be enhanced, but the basis is there and it works, at least for me.

Automatic deployment is done through multiple scripts. I saw some potential use for scripts outside of this.

There is a parent script which serves the purpose of accepting all the input parameters and passing those parameters to other scripts and calling the scripts in the correct order. The input parameters extensive but any pre configuration is avoided.


## **Prerequisites**

- Initial IIS setup is done - this script is for redeploying. Creating initial IIS config (bindings, sites, etc.) should be done prior.
- PowerShell does require setup in order to access the VPS. Guide on how to do this can be found [here](https://www.microsoft.com/en-gb/industry/blog/technetuk/2016/02/11/configuring-winrm-over-https-to-enable-powershell-remoting/).
- The scripts should be kept in a single folder.


## **Parameters**

I'll take a couple of moments to clearly explain parameters as they serve as scripts configuration.

- -scriptDir <scripts\_location> - scripts location. Mandatory.
- -angularDir <angular\_app\_location> - Angular app location. Mandatory.
- -repoDir <repository\_location> - Repo location. There's also a script that copies files to a repository location but excludes node\_modules and .angular folder. This is my preferred way to push projects into a repository. Not mandatory.
- -netDir <.net\_location> - .net app location. Mandatory.
- -publishDir <publish\_location> - Defines .NET publish output directory. Mandatory.
- -computerName <vps\_ip\_address> - Mandatory.
- -username <vps\_username> - Mandatory.
- -passwordLocation <vps\_password\_location> - The password should be set in a .txt file and it's location set here. Mandatory.
- -sessionAngularDir <vps\_angular\_location> - Output directory for file transfer to VPS. Mandatory
- -sessionNetDir <vps\_.net\_location> - Output directory for file transfer to VPS. Mandatory.
- -angularSiteName <angular\_site\_name> - Mandatory.
- -netSiteName <.net\_site\_name> - Mandatory.



## **How to run - command**
```shell
cd <scripts_location>

.\auto_deploy_iis.ps1 `
-scriptDir <scripts_location>`
-angularDir <angular_app_location>`
-repoDir <repository_location>`
-netDir <.net_location>`
-publishDir <publish_location>`
-computerName <vps_ip_address>`
-username <vps_username>`
-passwordLocation <vps_password_location>`
-sessionAngularDir <vps_angular_location>`
-sessionNetDir <vps_.net_location>`
-angularSiteName <angular_site_name>`
-netSiteName <.net_site_name> 
```


