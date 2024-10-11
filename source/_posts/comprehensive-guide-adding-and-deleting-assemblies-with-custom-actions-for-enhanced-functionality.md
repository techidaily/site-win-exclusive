---
title: "Comprehensive Guide: Adding and Deleting Assemblies with Custom Actions for Enhanced Functionality"
date: 2024-10-06T18:28:25.528Z
updated: 2024-10-11T02:28:04.996Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: "This Article Describes Comprehensive Guide: Adding and Deleting Assemblies with Custom Actions for Enhanced Functionality"
thumbnail: https://thmb.techidaily.com/a61ebba6dd861c81a2aafc9ac2f5e19d276c2c98436797dfa7a745296f54d142.jpg
---

## Comprehensive Guide: Adding and Deleting Assemblies with Custom Actions for Enhanced Functionality

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## DLL/OCX register/unregister

Object Linking and Embedding (OLE) is a proprietary Microsoft technology that allows developers to embed and link to other objects. With OLE Control Extension (OCX), you can develop and use custom user interface elements. You can also achieve OLE controls via Dynamic-Link Library(.dll) files.

However, to make sure the data transfer between applications work , these OLE controls must be registered on the system. How can we do that? That's what we will show you in this article.

### What is the Regsvr32 tool?

Regsvr32 is a command-line utility that allows registering and unregistering OLE controls such as DLLs and ActiveX controls in the Windows Registry. Regsvr32 can be found in:

* For 64-bit version: %systemroot%\\System32\\regsvr32.exe
* For 32-bit version: %systemroot%\\SysWoW64\\regsvr32.exe

The syntax of the Regsvr32 is actually quite simple:

Regsvr32 \[/u\] \[/n\] \[/i\[:cmdline\]\] <dllname>

/u - Unregister control

/i - Call DllInstall passing it an optional \[cmdline\]; when it is used with /u, it calls dll uninstall

/n - do not call DllRegisterServer; this option must be used with /i

/s – Silent

/e - Suppress only the GUI success message but shows the GUI error message

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)Regsvr32 must always be used from an elevated command prompt.

<!-- affiliate ads begin -->
<span id="1993645">
					<video width="576" height="240" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1993645.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/22993-1993645">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1993645.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:360px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fhomestyler.sjv.io%2Fc%2F5597632%2F1993645%2F22993'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1993645/22993" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

For example, to register a DLL/OCX, you can use:

Regsvr32.exe PATHTODLL\name.DLL

Copy

To unregister a DLL/OCX, you can use:

Regsvr32.exe /U PATHTODLL\name.DLL

Copy

![Regsvr32 command-line utility](https://cdn.advancedinstaller.com/img/register-unregister-dll-ocx-files/regsvr32.png "Regsvr32 command-line utility")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2049369/7443" target="_top" id="2049369">
  <img src="//a.impactradius-go.com/display-ad/7443-2049369" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2049369/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### How to Register DLL/OCX with VBscript?

Now that we know about the Regsvr32 utility, we can build the following scenario. Let's assume that we have a DLL in our project which will be installed in %systemroot%\\DLL. So, we can create the following registration script:

Option Explicit
On Error Resume Next
Dim strCmd,WshShell,strInstalldir
Set WshShell = CreateObject("WScript.Shell")
strSysRoot = WshShell.ExpandEnvironmentStrings("%SYSTEMROOT%")
strInstalldir = strSysRoot & "\DLL"
strCmd = "regsvr32.exe " & chr(34) & strInstalldir & "\libifcoremd.dll" & chr(34)& “ /s”
WshShell.Run strCmd

Copy

The script performs the following actions:

* Option Explicit: This statement enforces variable declaration in the script, ensuring that all variables are explicitly declared before they are used.
* On Error Resume Next: This statement allows the script to continue running even if an error occurs, bypassing the error and continuing with the next line of code.
* Dim strCmd, WshShell, strInstalldir: Declares three variables: strCmd to hold the command to be executed, WshShell to access the Windows Script Host Shell object, and strInstalldir to store the path to the DLL file.
* Set WshShell = CreateObject("WScript.Shell"): Creates an instance of the Windows Script Host Shell object, which allows the script to run shell commands and interact with the Windows environment.
* strSysRoot = WshShell.ExpandEnvironmentStrings("%SYSTEMROOT%"): Retrieves the value of the %SYSTEMROOT% environment variable using the ExpandEnvironmentStrings method of the WshShell object. The %SYSTEMROOT% variable represents the path to the Windows installation directory.
* strInstalldir = strSysRoot & "\\DLL": Constructs the path to the DLL file by appending the "\\DLL" folder to the strSysRoot variable. This assumes that the DLL file is located in the "DLL" folder within the Windows installation directory.
* strCmd = "regsvr32.exe " & chr(34) & strInstalldir & "\\libifcoremd.dll" & chr(34) & " /s": Constructs the command to be executed. It uses the regsvr32.exe utility to register a DLL file (libifcoremd.dll). The path to the DLL file is obtained by combining strInstalldir with the relative path \\libifcoremd.dll. The chr(34) is used to insert double quotes into the command string, and /s is a parameter to silently register the DLL without displaying any user interface.
* WshShell.Run strCmd: Executes the command stored in the strCmd variable using the Run method of the WshShell object. This runs the command in a separate process.

To unregister the DLL, we can use the following script:

Option Explicit
On Error Resume Next
Dim strCmd,WshShell,strInstalldir
Set WshShell = CreateObject("WScript.Shell")
strSysRoot = WshShell.ExpandEnvironmentStrings("%SYSTEMROOT%")
strInstalldir = strSysRoot & "\DLL"
strCmd = "regsvr32.exe /U " & chr(34) & strInstalldir & "\libifcoremd.dll" & chr(34)& “ /s”
WshShell.Run strCmd

Copy

* Now that the scripts are created, we need to open Advanced Installer and navigate to the Custom Actions page.
* There, search for the **Launch attached file** predefined custom action and add it into the sequence.
* Select your previously created registration script and configure the custom action as follows:

![register the DLL](https://cdn.advancedinstaller.com/img/register-unregister-dll-ocx-files/DLLRegisterVB.png "register the DLL")  

We also want to unregister the DLL during uninstallation, so let's create another custom action the same way as we did previously. Except this time, select the unregister script and configure the Custom Action as seen below:

![unregister the DLL during uninstallation](https://cdn.advancedinstaller.com/img/register-unregister-dll-ocx-files/DLLUnregisterVB.png "unregister the DLL during uninstallation")  

And that is it, all you need to do is **Build the MSI and install it.** The DLL will be registered.

### How to Register DLL/OCX with PowerShell?

Using the same logic as above, we can construct the following script to register a DLL with PowerShell:

$Arguments = "C:\Windows\DLL\libifcoremd.dll", "/s"
Start-Process -FilePath 'regsvr32.exe' -Args $Arguments -Wait -NoNewWindow -PassThru

Copy

The script performs the following actions:

* $Arguments: Declares a variable to hold the arguments for the regsvr32.exe command and assigns the arguments to be passed to the regsvr32.exe command. The first argument is the path to the DLL file (C:\\Windows\\DLL\\libifcoremd.dll), and the second argument (/s) is a parameter to silently register the DLL without displaying any user interface.
* Start-Process -FilePath 'regsvr32.exe' -Args $Arguments -Wait -NoNewWindow -PassThru: Executes the regsvr32.exe command using the Start-Process cmdlet. The -FilePath parameter specifies the path to the executable (regsvr32.exe). The -Args parameter specifies the arguments to be passed to the executable, which are stored in the $Arguments variable. The -Wait parameter ensures that the script waits for the command to complete before continuing. The -NoNewWindow parameter prevents the command from opening a new window. The -PassThru parameter returns an object representing the newly created process, allowing for further interaction if needed.

To unregister the DLL, we can use the following script:

$Arguments = “/u”,"C:\Windows\DLL\libifcoremd.dll", "/s"
Start-Process -FilePath 'regsvr32.exe' -Args $Arguments -Wait -NoNewWindow -PassThru

Copy

* When the scripts are created, we navigate to the Custom Actions page.
* Search for the **Run PowerShell script file** predefined Custom Action and add it in the sequence.
* Once we select the registration PowerShell script, we can proceed to configure the Custom Actions as follows:

![DLL Register PowerShell script](https://cdn.advancedinstaller.com/img/register-unregister-dll-ocx-files/DLLRegisterPS.png "DLL Register PowerShell script")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2151892/7443" target="_top" id="2151892">
  <img src="//a.impactradius-go.com/display-ad/7443-2151892" border="0" alt="https://techidaily.com" width="600" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2151892/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

For the unregister action, we follow the same steps as above and configure the Custom Actions:

![DLL Unregister PowerShell script](https://cdn.advancedinstaller.com/img/register-unregister-dll-ocx-files/DLLUnregisterPS.png "DLL Unregister PowerShell script")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2123728/7443" target="_top" id="2123728">
  <img src="//a.impactradius-go.com/display-ad/7443-2123728" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2123728/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

And you're done, now you can Build the MSI and install it. The DLL will be registered.

### How to Register DLL/OCX with Advanced Installer?

Advanced Installer makes it much easier to handle OLE control registration by providing a [Registration Tab GUI](https://tools.techidaily.com/advancedinstaller/products/). 

Accessing the GUI is quite easy with these steps:

1. First navigate to the [Files and Folders](https://tools.techidaily.com/advancedinstaller/products/) page
2. Add the DLL/OCX files.
3. Once the files are added, right-click on the DLL/OCX and select **Properties.**
4. Then, navigate to the Registration Tab.

![Register DLL/OCX with Advanced Installer](https://cdn.advancedinstaller.com/img/register-unregister-dll-ocx-files/DLLRegisterAI.png "Register DLL/OCX with Advanced Installer")  

As you may notice, there are three methods for registering files, two for native libraries and one for .NET assemblies.

\- Self-register native library

This file is marked for self-registration, however, the self-registration method for registering components has many drawbacks (like not being able to roll back the changes if something fails later in the install) and it is against Microsoft guidelines.

\- Extract registration info from the native library

All the necessary registry entries and keys are installed separately. You can see them in the [Registry](https://tools.techidaily.com/advancedinstaller/products/)and [COM](https://tools.techidaily.com/advancedinstaller/products/)pages. **This is the preferred way to register a file.**

\- Register .NET assembly for COM interoperability

It creates the required registry entries so that your assembly is operable through COM. You can see those registry entries in the Registry page.

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
<li><a href="https://facebook-clips.techidaily.com/new-in-2024-elite-zero-cost-fb-picturemovie-composer/"><u>[New] In 2024, Elite Zero-Cost FB Picture/Movie Composer</u></a></li>
<li><a href="https://instagram-videos.techidaily.com/new-in-2024-posting-vimeo-perfecting-your-instagram-content/"><u>[New] In 2024, Posting Vimeo Perfecting Your Instagram Content</u></a></li>
<li><a href="https://fox-friendly.techidaily.com/new-the-easy-guide-to-enhancing-images-via-iphone-cropping-for-2024/"><u>[New] The Easy Guide to Enhancing Images via iPhone Cropping for 2024</u></a></li>
<li><a href="https://youtube-lab.techidaily.com/ed-essential-tips-and-tricks-for-creating-killer-short-videos-on-yt-for-2024/"><u>[Updated] Essential Tips and Tricks for Creating Killer Short Videos on YT for 2024</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/exploring-shadows-online-a-beginners-guide-to-dark-and-deep-web-differences-tips-by-malwarefox/"><u>Exploring Shadows Online: A Beginner's Guide to Dark and Deep Web Differences, Tips by MalwareFox</u></a></li>
<li><a href="https://common-error.techidaily.com/feature-update-to-windows-10-version-1607-failed-to-install/"><u>Feature Update to Windows 10 Version 1607 Failed to Install</u></a></li>
<li><a href="https://driver-error.techidaily.com/hidef-audio-resolved-successful-fix/"><u>HiDef Audio Resolved: Successful Fix</u></a></li>
<li><a href="https://fox-blue.techidaily.com/in-2024-the-dichotomy-of-digital-immersion-in-vr/"><u>In 2024, The Dichotomy of Digital Immersion in VR</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/solving-video-capture-problems-in-windows-10-gaming-effective-fixes-and-guides/"><u>Solving Video Capture Problems in Windows 10 Gaming: Effective Fixes and Guides</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/step-by-step-guide-how-to-erase-shadows-from-images-successfully/"><u>Step-by-Step Guide: How To Erase Shadows From Images Successfully</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/step-by-step-guide-mirroring-your-iphone-screen-on-apple-tv/"><u>Step-by-Step Guide: Mirroring Your iPhone Screen on Apple TV</u></a></li>
</ul></div>

