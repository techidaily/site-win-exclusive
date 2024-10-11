---
title: Step-by-Step Guide to Implementing Non-Signed Kernel Drivers via Custom Scripts
date: 2024-10-08T23:41:21.142Z
updated: 2024-10-11T03:04:35.291Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: This Article Describes Step-by-Step Guide to Implementing Non-Signed Kernel Drivers via Custom Scripts
thumbnail: https://thmb.techidaily.com/4b7359aaf8e940a96bfa42de92bb50e50f03e20d48a13d1d95464ad526124572.jpg
---

## Step-by-Step Guide to Implementing Non-Signed Kernel Drivers via Custom Scripts

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Install Unsigned Drivers

There are cases when we try to install drivers on Windows and the following windows appears:

![signerror when try to install drivers on Windows](https://cdn.advancedinstaller.com/img/install-unsigned-drivers-using-custom-actions/signerror.png "signerror when try to install drivers on Windows")  

And we must click : "Install this driver software anyway". 

This is happening because that particular driver is unsigned. In the IT Pros world we need to make sure that these types of drivers are installed silently and no interaction to the user is necessary. We can install the driver without any prompt in following way :

Tools that you need: (most are from the Windows Driver Kit – the latest version of [Windows Driver Kit W11 22H2](https://learn.microsoft.com/en-us/windows-hardware/drivers/download-the-wdk "Windows Driver Kit W11 22H2")):

[Inf2Cat.exe](https://learn.microsoft.com/en-us/windows-hardware/drivers/devtest/inf2cat "Inf2Cat.exe") (To generate the unsigned catalog file from our INF)

[Makecert.exe](https://learn.microsoft.com/en-us/windows/win32/seccrypto/makecert "Makecert.exe") (Used to create our certificate)

[Signtool.Exe](https://learn.microsoft.com/en-us/windows/win32/seccrypto/signtool "Signtool.Exe") (Sign our catalog file with an Authenticode digital signature)

[Certmgr.exe](https://learn.microsoft.com/en-us/dotnet/framework/tools/certmgr-exe-certificate-manager-tool "Certmgr.exe") (Used to add and delete our certificate to the system root)

Let's have a look at each step that you must take to get your unsigned certificates installed silently. 

### Create a digital certificate by using the MakeCert tool

Open an **x86/x64 Free Build Environment** command prompt with administrator permissions, by right-clicking **x86 Free Build Environment** on the **Start menu**, and then selecting **Run as administrator**.

At the **x86/x64 Free Build Environment** command prompt, type the following command on a single line (it appears here on multiple lines for clarity and to fit space limitations):

makecert -r -n "CN=Name"
		 -ss CertStore
		 -sr LocalMachine

Copy

Ex: makecert -r -n CN="TestCert" -ss Root -sr LocalMachine

The meaning of each parameter is as follows:

**\-r**

Specifies that the certificate is to be "self-signed," rather than signed by a CA. Also called a "root" certificate.

**\-n** "CN= Name "

Specifies the name associated with this new certificate. It is recommended that you use a certificate name that clearly identifies the certificate and its purpose.

**\-ss** CertStore

Specifies the name of the certificate store in which the new certificate is placed.

**\-sr** LocalMachine

Specifies that the certificate store created by the -ss option is in the per computer store, instead of the default per user store.

![Specifies that the certificate store](https://cdn.advancedinstaller.com/img/install-unsigned-drivers-using-custom-actions/makecert.png "Specifies that the certificate store")  

The command returns the message "Succeeded" when the store and certificate are created.

### Create a .cat (catalog) file for the driver

We notice that some drivers don't contain a cat file, so we'll need to generate one. 

Open the .INF file in a text editor. Ensure that under the \[version\] section that you have an entry specifying a .cat file. 

If it's not there, add the lineat the end of the section. For example:

[version]Signature=xxxxxxProvider=xxxxxxCatalogFile=MyCatalogFile.cat

Copy

"MyCatalogFile.cat" is the name of the cat file that we want to generate. Not having a line specifying this will result in an "error 22.9.4 - Missing 32-bit catalog file entry" when we run Inf2Cat.exe. 

Command line:

Inf2Cat.exe /driver:"<Path to folder containing driver files

Copy

Ex : Inf2cat.exe /driver:\[PathToINFwithoutFile\] /os:10\_x64,10\_x86

The meaning of each parameter is as follows:

\- **/driver**: c:\\toaster\\device

Specifies the location of the .inf file for the driver package. You must specify the complete folder path. A '.' character does not work here to represent the current folder.

\- **/os**: 10\_x86 or 10\_x64

Identifies the 32-bit version of Windows 10 as the operating system. Run the command inf2cat /? for a complete list of [supported operating systems and their codes](https://learn.microsoft.com/en-us/windows-hardware/drivers/devtest/inf2cat "supported operating systems and their codes").

![Identifies the 32-bit version of Windows 10](https://cdn.advancedinstaller.com/img/install-unsigned-drivers-using-custom-actions/inf2cat.png "Identifies the 32-bit version of Windows 10")  

<!-- affiliate ads begin -->
<span id="1975562">
					<video width="128" height="480" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1975562.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/22993-1975562">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1975562.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:80px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fhomestyler.sjv.io%2Fc%2F5597632%2F1975562%2F22993'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1975562/22993" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Sign the catalog file using SignTool

signtool sign /v /sm /s Root /n "TestCert" /t http://timestamp.digicert.com path\example.cat

Copy

The meaning of each parameter is as follows:

\- **/sm**

Specifies that a machine store, instead of a user store, is used

\- **/s** CertStore

Specifies the name of the certificate store in which SignTool searches for the certificate specified by the parameter /n. In our case we look in the Root

\- **/n** “Name ”

Specifies the name of the certificate to be used to sign the package. You must include enough of the name to allow SignTool to distinguish it from others in the store. If this name includes spaces, then you must surround the name with double quotes.

\- **/t** path to time stamping service

Specifies the path to a time stamping service at an approved certification authority. If you purchase your certificate from a commercial vendor, they should provide you with the appropriate path to their service.

\- example.cat

Specifies the path and file name of the catalog file to be signed.

Signtool indicates completion with the following message:

![Successfully signed and timestamped](https://cdn.advancedinstaller.com/img/install-unsigned-drivers-using-custom-actions/signtool.png "Successfully signed and timestamped")  

Successfully signed and timestamped: C:\\toaster\\device\\example.cat

### Export the certificate from certstore manually

Run an administrator command: certmgr.exe

Export the certificate manually:

![Export the certificate manually](https://cdn.advancedinstaller.com/img/install-unsigned-drivers-using-custom-actions/exportcert.png "Export the certificate manually")  

<!-- affiliate ads begin -->
<span id="1993652">
					<video width="576" height="240" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1993652.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/22993-1993652">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1993652.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:360px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fhomestyler.sjv.io%2Fc%2F5597632%2F1993652%2F22993'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1993652/22993" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Install the certificate to Root and TrustedPublisher

Command line:

certutil.exe -addstore "Root" [PathToCertificatewithFile]
certutil.exe -addstore "TrustedPublisher" [PathToCertificatewithFile]

Copy

![Install the certificate to Root and TrustedPublisher](https://cdn.advancedinstaller.com/img/install-unsigned-drivers-using-custom-actions/addcertificate.png "Install the certificate to Root and TrustedPublisher")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1938682/19272" target="_top" id="1938682">
  <img src="//a.impactradius-go.com/display-ad/19272-1938682" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1938682/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

for remove :

certutil.exe -delstore "Root" [PathToCertificatewithFile]
certutil.exe -delstore "TrustedPublisher" [PathToCertificatewithFile]

Copy

Now we can install the driver without the prompt.

### Build the MSI

Now that we have understood how you sign a driver we also need to learn how you add the actions in the MSI. Basically all you need are two steps:

1. Install the certificate
2. Install the driver

For the second step we already had a look [a chapter earlier](https://tools.techidaily.com/advancedinstaller/products/) on how to achieve that, so basically all we have to do is create a script that performs the certutil commands previously mentioned. Let’s assume that the driver .inf name is HP.inf and let’s assume that we are going to place the certificate directly into the C:\\Windows\\DPInst.

For VBScript:

Option Explicit
On Error Resume Next
Dim strCmd,WshShell,strInstalldir
Set WshShell = CreateObject("WScript.Shell")
strInstalldir = WshShell.ExpandEnvironmentStrings("%SYSTEMROOT%")
strCmd = "certutil.exe -addstore " & chr(34) & "Root" & chr(34) & " " & chr(34) & strInstalldir & "\DPInst\TestCer.cer" & chr(34)
WshShell.Run strCmd

Copy

The script performs the following actions:

* Option Explicit: This statement enforces variable declaration in the script, ensuring that all variables are explicitly declared before they are used.
* On Error Resume Next: This statement allows the script to continue running even if an error occurs, bypassing the error and continuing with the next line of code.
* Dim strCmd, WshShell, strInstalldir: Declares three variables: strCmd to hold the command to be executed, WshShell to access the Windows Script Host Shell object, and strInstalldir to store the expanded value of the %SYSTEMROOT% environment variable.
* Set WshShell = CreateObject("WScript.Shell"): Creates an instance of the Windows Script Host Shell object, which allows the script to run shell commands and interact with the Windows environment.
* strInstalldir = WshShell.ExpandEnvironmentStrings("%SYSTEMROOT%"): Retrieves the value of the %SYSTEMROOT% environment variable using the ExpandEnvironmentStrings method of the WshShell object. The %SYSTEMROOT% variable represents the path to the Windows installation directory.
* strCmd = "certutil.exe -addstore " & chr(34) & "Root" & chr(34) & " " & chr(34) & strInstalldir & "\\DPInst\\TestCer.cer" & chr(34): Constructs the command to be executed. It uses the certutil.exe utility to add a certificate (TestCer.cer) to the "Root" certificate store. The path to the certificate file is obtained by combining strInstalldir (Windows installation directory) with the relative path \\DPInst\\TestCer.cer. The chr(34) is used to insert double quotes into the command string.
* WshShell.Run strCmd: Executes the command stored in the strCmd variable using the Run method of the WshShell object. This runs the command in a separate process.

In summary, the script uses VBScript to execute the certutil.exe command and add a certificate (TestCer.cer) to the "Root" certificate store. The script retrieves the Windows installation directory, constructs the command with the appropriate paths and options, and then runs it using the WshShell object.

Once the script is created, navigate to the Custom Actions Page and add the **Launch attached file** predefined custom action into the sequence, select the installation vbscript file that was previously created and configure the Custom Action as such:

![add certificate](https://cdn.advancedinstaller.com/img/install-unsigned-drivers-using-custom-actions/addcertAI.png "add certificate")  

![Important](https://cdn.advancedinstaller.com/svg/common/IconMessageInfo.svg)Make sure that the script which installs the certificate is placed before the script which installs the driver under the “Install Execution Stage” section.

With PowerShell it's even easier because we can use the [Import-Certificate cmdlet](https://learn.microsoft.com/en-us/powershell/module/pki/import-certificate?source=recommendations&amp;view=windowsserver2022-ps "Import-Certificate cmdlet"):

$CerLocation = $env:SystemRoot + "\DPInst\TestCer.cer"
Import-Certificate -FilePath $CerLocation -CertStoreLocation Cert:\LocalMachine\Root
Import-Certificate -FilePath $CerLocation -CertStoreLocation Cert:\LocalMachine\TrustedPublisher

Copy

Once we have the script ready, navigate to the Custom Actions Page and add the **Run PowerShell script file** predefined custom action into the sequence, select **Attached Script** and select the file that was previously created and configure the Custom Action as such:

![PowerShell script file - Attached Script](https://cdn.advancedinstaller.com/img/install-unsigned-drivers-using-custom-actions/addcertAIPS.png "PowerShell script file - Attached Script")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2087267/19272" target="_top" id="2087267">
  <img src="//a.impactradius-go.com/display-ad/19272-2087267" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2087267/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Next, build the package and during installation/uninstallation the PowerShell scripts will run and install/uninstall the driver without asking if we want to install an unsigned driver.

<!-- affiliate ads begin -->
<a href="https://ephamedtechinc.pxf.io/c/5597632/2137220/26400" target="_top" id="2137220">
  <img src="//a.impactradius-go.com/display-ad/26400-2137220" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://ephamedtechinc.pxf.io/i/5597632/2137220/26400" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Installing unsigned drivers with Advanced Installer

As you can see, handling unsigned certificates is not an easy task and it’s definitely time consuming. Advanced Installer makes it easier to install unsigned drivers with just a click of a button..and yes that is not a figure of speech.

Navigate to the Drivers page and click on **New Driver**. A window will open for you to select the .inf file which must be present in the package.

![Installing unsigned drivers with Advanced Installer](https://cdn.advancedinstaller.com/img/install-unsigned-drivers-using-custom-actions/advinstdriverinst.png "Installing unsigned drivers with Advanced Installer")  

Next, all you have to do is just select “Install unsigned driver packages and driver packages that have missing files” and Advanced Installer does everything for you!

![Install unsigned driver packages and driver packages that have missing files](https://cdn.advancedinstaller.com/img/install-unsigned-drivers-using-custom-actions/unsigneddriversAI.png "Install unsigned driver packages and driver packages that have missing files")  

<!-- affiliate ads begin -->
<a href="https://bluettiit.sjv.io/c/5597632/2148127/17093" target="_top" id="2148127">
  <img src="//a.impactradius-go.com/display-ad/17093-2148127" border="0" alt="https://techidaily.com" width="120" height="90"/>
</a>
<img height="0" width="0" src="https://bluettiit.sjv.io/i/5597632/2148127/17093" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

And that is it! Next, just build and install the package and you should have a clean installation without any warning messages from the OS.

<ins class="adsbygoogle"
     style="display:block"
     data-ad-format="autorelaxed"
     data-ad-client="ca-pub-7571918770474297"
     data-ad-slot="1223367746"></ins>

<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-7571918770474297"
     data-ad-slot="8358498916"
     data-ad-format="auto"
     data-full-width-responsive="true"></ins>

<span class="atpl-alsoreadstyle">Also read:</span>
<div><ul>
<li><a href="https://instagram-video-recordings.techidaily.com/new-2024-approved-get-paid-on-instagram-the-leading-money-making-strategies/"><u>[New] 2024 Approved Get Paid on Instagram The Leading Money-Making Strategies</u></a></li>
<li><a href="https://some-knowledge.techidaily.com/new-experience-the-thrill-of-kinemaster-and-rank-10-online-alternatives-alike/"><u>[New] Experience the Thrill of KineMaster and Rank 10 Online Alternatives Alike</u></a></li>
<li><a href="https://some-skills.techidaily.com/new-how-to-choose-the-background-music-for-the-trailer/"><u>[New] How to Choose the Background Music for the Trailer</u></a></li>
<li><a href="https://screen-mirroring-recording.techidaily.com/2024-approved-how-to-get-the-most-out-of-your-streamlabs-obs-setup/"><u>2024 Approved How to Get the Most Out of Your Streamlabs OBS Setup</u></a></li>
<li><a href="https://youtube-webster.techidaily.com/approved-unveiling-the-secrets-to-effortless-youtube-sharing-on-fb-groups/"><u>2024 Approved Unveiling the Secrets to Effortless YouTube Sharing on FB Groups</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/expert-tips-and-tricks-for-effortless-screenshotting-on-macos-high-sierra/"><u>Expert Tips and Tricks for Effortless Screenshotting on macOS High Sierra</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/exploring-security-measures-the-reasons-behind-antivirus-software-choosing-to-quarantine-instead-of-deleting-potentially-dangerous-files/"><u>Exploring Security Measures: The Reasons Behind Antivirus Software Choosing to Quarantine Instead of Deleting Potentially Dangerous Files</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/guide-to-mastering-marvel-super-war-a-step-by-step-tutorial-for-pc-gamers/"><u>Guide to Mastering Marvel Super War: A Step-by-Step Tutorial for PC Gamers</u></a></li>
<li><a href="https://change-location.techidaily.com/in-2024-5-easy-ways-to-change-location-on-youtube-tv-on-samsung-galaxy-s24plus-drfone-by-drfone-virtual-android/"><u>In 2024, 5 Easy Ways to Change Location on YouTube TV On Samsung Galaxy S24+ | Dr.fone</u></a></li>
<li><a href="https://facebook-video-content.techidaily.com/most-popular-fb-videos-download-now-for-2024/"><u>Most Popular FB Videos - Download Now for 2024</u></a></li>
<li><a href="https://video-content-creator.techidaily.com/new-online-video-editors-compatible-with-chromebooks-2023-review-for-2024/"><u>New Online Video Editors Compatible with Chromebooks 2023 Review for 2024</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/optimizing-installation-processes-mastering-dependency-management-in-msi-creations-using-advanced-installer/"><u>Optimizing Installation Processes: Mastering Dependency Management in MSI Creations Using Advanced Installer</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/title-navigating-utorrents-legitimacy-unveiling-its-safety-and-protecting-againnst-malware-in-depth-review/"><u>Title: Navigating uTorrent's Legitimacy - Unveiling Its Safety & Protecting Againnst Malware [In-Depth Review]</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/top-rated-voice-separation-ai-tool-simplify-and-enhance-your-audio-editing/"><u>Top-Rated Voice Separation AI Tool: Simplify and Enhance Your Audio Editing</u></a></li>
<li><a href="https://extra-lessons.techidaily.com/ultimate-toolkit-turning-images-to-videos/"><u>Ultimate Toolkit Turning Images to Videos</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/unveiling-stalkerware-comprehensive-guide-for-detection-and-elimination-safenetadvisor/"><u>Unveiling Stalkerware: Comprehensive Guide for Detection & Elimination - SafeNetAdvisor</u></a></li>
</ul></div>

