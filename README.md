## Download Windows Admin Center

Updated: July 5, 2025       
**⬇️ [Download Windows Admin Center](*)**

You can update non-preview versions of Windows Admin Center either through Microsoft Update or by manually downloading and installing the latest version. Each non-preview release is supported until 30 days after the release of the next non-preview version. For more details, refer to our support policy.


## Prerequisites

To install Windows Admin Center, the following prerequisites are required:

* A Windows PC or server on which to install Windows Admin Center.

* Administrative privileges or equivalent permissions on the target machine.

* Optional: An SSL certificate for *Server Authentication (1.3.6.1.5.5.7.3.1)*. While a self-signed certificate can be used for testing purposes, production environments should use a certificate issued by a trusted certificate authority. If you don’t have a certificate, the Windows Admin Center installer can generate a self-signed certificate valid for 60 days.

## Determine your installation type

Review the [installation options](*) which includes the [supported operating systems](*). To install Windows Admin Center on a virtual machine in Azure, see [Deploy Windows Admin Center in Azure](*).

## Install Windows Admin Center

### Desktop Experience

To install Windows Admin Center on a machine running Windows Server Desktop Experience, follow these steps:

1. Open the **Start** menu and type **Windows Admin Center Setup** in the search bar.

2. From the **Best match** list, select the **Windows Admin Center Setup** app.

3. In the **Get started with Windows Admin Center** window, if you agree to the license terms, click **Next** to proceed.

4. The latest installer will download automatically and be saved to your *Downloads* folder. Once the download finishes, click **Install** to launch the installer from the Downloads folder.

5. On the **Welcome to the Windows Admin Center setup wizard** window, click **Next** to continue.

6. On the **License Terms and Privacy Statement** window, if you agree to the terms, select **I accept these terms and understand the privacy statement**, then click **Next** to begin the installation.

7. In the **Select installation mode** window, choose **Express setup**, then click **Next**.

8. In the **Select TLS certificate** window, pick the option that best fits your needs, then click **Next**.


 
> ### Note

> You need to choose which Transport Layer Security (TLS) certificate Windows Admin Center will use. If you already have a certificate, it must be installed in the `LocalMachine\My` certificate store. For testing purposes, the installer can create a self-signed certificate that expires after 60 days.

9. In the **Automatic updates** window, choose your preferred update setting, then click **Next**.

10. In the **Send diagnostic data to Microsoft** window, select your preferred option, then click **Next**.

11. Review the **Ready to install** window, then click **Install** to begin the installation.

12. Once the installation completes, select **Start Windows Admin Center**, then click **Finish**.

13. Sign in with administrator credentials to begin using Windows Admin Center.



### Server Core

To install Windows Admin Center on a machine running Windows Server Core or via PowerShell, follow these steps:

1. Sign in to your machine. On Server Core, open the SConfig menu, select option **15**, and press <kbd>Enter</kbd> to launch a PowerShell session. If using the Desktop Experience, remote desktop into your VM and open PowerShell.
2. Download the Windows Admin Center installer and copy it to your machine by running the following PowerShell command:

```powershell
$parameters = @{
     Source = "https://aka.ms/WACdownload"
     Destination = ".\WindowsAdminCenter.exe"
}
Start-BitsTransfer @parameters
```

3. To install Windows Admin Center, run the following command:

```powershell
Start-Process -FilePath '.\WindowsAdminCenter.exe' -ArgumentList '/VERYSILENT' -Wait
```

4. You may also need to start the Windows Admin Center service using the following command:

```powershell
Start-Service -Name WindowsAdminCenter
```

You've now installed Windows Admin Center on your machine.
