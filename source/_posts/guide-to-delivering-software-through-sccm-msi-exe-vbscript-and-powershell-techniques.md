---
title: "Guide to Delivering Software Through SCCM: MSI, EXE, VBScript & PowerShell Techniques"
date: 2024-10-09T23:40:53.702Z
updated: 2024-10-10T18:58:16.926Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: "This Article Describes Guide to Delivering Software Through SCCM: MSI, EXE, VBScript & PowerShell Techniques"
thumbnail: https://thmb.techidaily.com/8e48b2813408b75482794fbb8e9c7fd16cd8c115a0a176db85647e2b441ce187.jpg
---

## Guide to Delivering Software Through SCCM: MSI, EXE, VBScript & PowerShell Techniques

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Deploy with SCCM

SCCM is an abbreviation for System Center Configuration Manager. It is a comprehensive systems management solution offered by Microsoft for managing large-scale software, operating system, and device deployments. SCCM enables IT administrators to automate software installations, manage updates and patches, deploy operating systems to new machines, and perform a variety of other administrative tasks across a network.

SCCM provides a centralized console through which administrators can efficiently manage and monitor software and hardware resource deployment and configuration. It includes inventory management, software distribution, patch management, remote control, and reporting capabilities. SCCM integrates with Active Directory to enable targeted deployments based on user and device information.

Administrators can use SCCM to create packages and programs that can be used to deploy software applications, perform system updates, and manage configurations across multiple devices such as desktops, laptops, servers, and mobile devices. It supports both on-premises and cloud-based deployments, giving organizations of all sizes flexibility.

SCCM is critical for streamlining IT operations, reducing manual efforts, ensuring compliance, and ensuring a standardized and secure computing environment. It enables organizations to manage their software and hardware assets more efficiently, improve security and compliance, and simplify the process of deploying and managing systems across the enterprise.

When it comes to SCCM, there are two methods for deploying packages. If the package is an MSI, the steps are much simpler, as shown below. Of course, if you want to use wrappers or EXE bundles, you can, but there are some extra steps to take.

### Deploy MSI via SCCM

To deploy an MSI via SCCM, go to Software Library -> Application Management -> Applications -> right click Create Application

![sccm create application](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application.png "sccm create application")  

Because the source is an MSI, choose Windows Installer and browse for source content

![sccm create application msi](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-msi.png "sccm create application msi")  

This warning is present with most MSI packages, so we can click YES:

![sccm create application msi warning](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-msi-warning.png "sccm create application msi warning")  

<!-- affiliate ads begin -->
<a href="https://bluettius.sjv.io/c/5597632/2139114/17108" target="_top" id="2139114">
  <img src="//a.impactradius-go.com/display-ad/17108-2139114" border="0" alt="https://techidaily.com" width="468" height="60"/>
</a>
<img height="0" width="0" src="https://bluettius.sjv.io/i/5597632/2139114/17108" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

The next steps require only to acknowledge what is going to be created so click Next until the wizard is finished.

![sccm create application msi info](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-msi-info.png "sccm create application msi info")  

![sccm create application msi general info](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-msi--general-info.png "sccm create application msi general info")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2100537/7443" target="_top" id="2100537">
  <img src="//a.impactradius-go.com/display-ad/7443-2100537" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2100537/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

![sccm create application msi completion](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-msi-completion.png "sccm create application msi completion")  

An that is it, all that is left to be done is to distribute the package content on all available Distribution Points and deploy the packaged to the desired list of devices/users in the infrastructure.

<!-- affiliate ads begin -->
<a href="https://25home.pxf.io/c/5597632/2148639/16836" target="_top" id="2148639">
  <img src="//a.impactradius-go.com/display-ad/16836-2148639" border="0" alt="https://techidaily.com" width="180" height="90"/>
</a>
<img height="0" width="0" src="https://25home.pxf.io/i/5597632/2148639/16836" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Deploy EXE/VBscript/PowerShell via SCCM

When it comes to other forms of installers, there are a few additional steps which need to be taken. First, go to Software Library -> Application Management -> Applications -> right click Create Application

![sccm create application](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application.png "sccm create application")  

We will have to choose Manually specify the application information, which will give you the option to choose Script Installer later on this wizard.

![sccm create application script manual](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-manual.png "sccm create application script manual")  

Next, fill in all the information for the General Information tab. Keep in mind that “Name” is only an internal information in SCCM and not what the user sees in Software Center.

![sccm create application script general information](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-general-information.png "sccm create application script general information")  

Next, select English default and remove all other languages if not specifically mentioned otherwise. The Localized application name is the name shown is Software Center:

![sccm create application script selected language](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-selected-language.png "sccm create application script selected language")  

We will need to create a deployment type. A deployment type includes all of the information and instructions required for SCCM to successfully install and manage the application. Details such as the installation command, installation behavior, requirements, detection methods, and user experience settings are all included. SCCM supports a variety of deployment types to accommodate a variety of application scenarios and deployment needs.

![sccm create application script create deployment](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-create-deployment.png "sccm create application script create deployment")  

When we reach the specify settings dialog, we choose again Script Installer:

![sccm create application script select script installer](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-select-script-installer.png "sccm create application script select script installer")  

Next, we fill in the application deployment type name:

![sccm create application script deployment name](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-deployment-name.png "sccm create application script deployment name")  

Now is the part where we add the Content location from the master share and the install and uninstall lines.

![sccm create application script deployment content location](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-deployment-content-location.png "sccm create application script deployment content location")  

<!-- affiliate ads begin -->
<span id="1912746">
					<video width="240" height="200" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1912746.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/20231-1912746">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1912746.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:150px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fmindmanager.sjv.io%2Fc%2F5597632%2F1912746%2F20231'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1912746/20231" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

On the next tab, add the detection method. The detection method checks for the existence of an application using specific criteria or rules. When you deploy an application in SCCM, you define a detection method to ensure that the application is only installed on devices that require it, or to determine whether an upgrade or update is needed.

The detection method can be configured to use various criteria, such as:

* File or Folder Detection: SCCM can check the device for the presence of a specific file or folder. It can look for the presence of an executable file, a configuration file, or a specific folder structure associated with the application, for example.
* Registry Key Detection: SCCM can check the device for the presence or value of a specific registry key. This is frequently used to identify applications that generate specific registry entries during installation.
* Windows Installer Detection: SCCM can use the Windows Installer database (MSI) to see if a particular product code, package code, or product version is already installed on the device.
* Custom Script Detection: Custom scripts (VBScript, PowerShell, etc.) can be used to define detection logic in SCCM. Administrators can create scripts to perform complex checks based on their needs.

With the MSI deployment method, this is easy because SCCM uses the Windows Installer detection which checks for the presence of the product code, and these steps which we are doing here are skipped. In case your package contains an MSI it is recommended to use the Windows Installer Detection.

![sccm create application script detection method](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-detection-method.png "sccm create application script detection method")  

<!-- affiliate ads begin -->
<a href="https://unicoeye.pxf.io/c/5597632/2134492/18498" target="_top" id="2134492">
  <img src="//a.impactradius-go.com/display-ad/18498-2134492" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://unicoeye.pxf.io/i/5597632/2134492/18498" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

![sccm create application script detection method options](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-detection-method-options.png "sccm create application script detection method options")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2151894/7443" target="_top" id="2151894">
  <img src="//a.impactradius-go.com/display-ad/7443-2151894" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2151894/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Next, we reach the user experience settings. The configuration options that determine how an application installation or update is presented and handled on end-user devices are referred to as user experience settings with applications. Administrators can use these settings to customize the behavior and appearance of application deployments in order to provide a consistent user experience. The following are some of the most common user experience settings available in SCCM:

* Install for User or System: This setting determines whether the application is installed per user or per system. Per-user installation installs the application for the currently logged-on user, whereas per-system installation installs it for all users on the device.
* Install Whether or Not a User is Logged On: Determines whether the application installation should continue even if no user is currently logged in.
* Allow Users to Interact with the Installation: Allows or disables user interaction with the installation process, such as displaying or suppressing installation prompts or dialogs.

The most used configuration options for these step are:

* Installation behavior: Install for system (runs under NT System/Administrator account)
* Logon requirement: Whether or not a user is logged in
* Installation program visibility: Normal
* Allow users to view and interact with the program installation: Checked

![sccm create application script user experience](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-user-experience.png "sccm create application script user experience")  

Click next and add installation requirements if needed and dependency application

![sccm create application script dependencies](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-dependencies.png "sccm create application script dependencies")  

In the final part, click Next until everything is done.

![sccm create application script confirm deployment](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-confirm-deployment.png "sccm create application script confirm deployment")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1884021/19272" target="_top" id="1884021">
  <img src="//a.impactradius-go.com/display-ad/19272-1884021" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1884021/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

![sccm create application script confirm deployment success](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-confirm-deployment-success.png "sccm create application script confirm deployment success")  

![sccm create application script confirm application creation](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-confirm-application-creation.png "sccm create application script confirm application creation")  

<!-- affiliate ads begin -->
<a href="https://aidotcom.pxf.io/c/5597632/2129042/19576" target="_top" id="2129042">
  <img src="//a.impactradius-go.com/display-ad/19576-2129042" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aidotcom.pxf.io/i/5597632/2129042/19576" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

![sccm create application script confirm application creation success](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-confirm-application-creation-success.png "sccm create application script confirm application creation success")  

And that is it. As with MSI deployments, all that remains is to distribute the package content to all available Distribution Points and deploy the package to the desired list of infrastructure devices/users.

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
<li><a href="https://youtube-lab.techidaily.com/024-approved-monetizing-makeup-tutorial-content/"><u>[New] 2024 Approved Monetizing Makeup Tutorial Content</u></a></li>
<li><a href="https://youtube-docs.techidaily.com/implifying-social-media-your-guide-to-facebook-youtube-syncing/"><u>[New] Simplifying Social Media Your Guide to Facebook-YouTube Syncing</u></a></li>
<li><a href="https://driver-download.techidaily.com/1722971187990-accelerate-your-work-with-rapidly-downloaded-drivers-for-the-dell-latitude-e6-420/"><u>Accelerate Your Work with Rapidly Downloaded Drivers for the Dell Latitude E6 420</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/comparative-techniques-in-software-remastering-insights-into-msi-and-exe-conversion-strategies/"><u>Comparative Techniques in Software Remastering: Insights Into MSI and EXE Conversion Strategies</u></a></li>
<li><a href="https://buynow-marvelous.techidaily.com/comprehensive-evaluation-of-the-google-pixel-4a-the-ideal-choice-for-casual-users/"><u>Comprehensive Evaluation of the Google Pixel 4A: The Ideal Choice for Casual Users</u></a></li>
<li><a href="https://blog-min.techidaily.com/how-to-recover-lost-calendar-on-iphone-13-stellar-by-stellar-data-recovery-ios-iphone-data-recovery/"><u>How to Recover lost Calendar on iPhone 13 | Stellar</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/id3-tagger-quickly-assign-metadata-to-your-audio-library-for-enhanced-discoverability/"><u>ID3 Tagger: Quickly Assign Metadata to Your Audio Library for Enhanced Discoverability</u></a></li>
<li><a href="https://android-location-track.techidaily.com/in-2024-3-solutions-to-find-your-google-pixel-fold-current-location-of-a-mobile-number-drfone-by-drfone-virtual-android/"><u>In 2024, 3 Solutions to Find Your Google Pixel Fold Current Location of a Mobile Number | Dr.fone</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/mastering-service-setup-and-configuration-with-microsofts-msi-packaging-techniques/"><u>Mastering Service Setup & Configuration with Microsoft's MSI Packaging Techniques</u></a></li>
<li><a href="https://screen-mirroring-recording.techidaily.com/mastering-the-art-of-screenshot-with-zd-software-for-2024/"><u>Mastering the Art of Screenshot with ZD Software for 2024</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/say-goodbye-to-unwanted-locker-pops-ups-securely-clean-adware-off-your-android-using-malwarefox-tips/"><u>Say Goodbye to Unwanted Locker Pops-Ups: Securely Clean Adware Off Your Android Using MalwareFox Tips</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/top-5-multifaceted-antivirus-scanners-expert-reviews-and-comparisons/"><u>Top 5 Multifaceted Antivirus Scanners: Expert Reviews and Comparisons</u></a></li>
<li><a href="https://solve-marvelous.techidaily.com/transformez-vos-fichiers-swf-en-avi-sans-frais-grace-au-convertisseur-en-ligne-movavi-solution-optimisee-seo/"><u>Transformez Vos Fichiers SWF en AVI Sans Frais Grâce Au Convertisseur en Ligne Movavi - Solution Optimisée SEO</u></a></li>
<li><a href="https://os-tips.techidaily.com/troubleshooting-iphones-how-to-overcome-the-persistent-charging-screen-problem/"><u>Troubleshooting iPhones: How to Overcome the Persistent Charging Screen Problem</u></a></li>
</ul></div>

