---
title: How to Distribute Executable, VBScript & PowerShell Packages with Microsoft Endpoint Configuration Manager (Intune)
date: 2024-10-07T21:41:02.400Z
updated: 2024-10-11T01:52:56.107Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: This Article Describes How to Distribute Executable, VBScript & PowerShell Packages with Microsoft Endpoint Configuration Manager (Intune)
thumbnail: https://thmb.techidaily.com/59f91e855b8da924b2a0ba83734da21e4ed3929e8ad5bcae0b9a32715b7cc063.jpg
---

## How to Distribute Executable, VBScript & PowerShell Packages with Microsoft Endpoint Configuration Manager (Intune)

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Deploy with Intune

Intune is a cloud-based service provided by Microsoft that focuses on mobile device management (MDM) and mobile application management. It is also known as Microsoft Intune or Microsoft Endpoint Manager (MAM). It is part of the Microsoft Endpoint Manager tool suite and is intended to assist organizations in managing and securing their devices, applications, and data across multiple platforms such as Windows, macOS, iOS, and Android.

Intune includes a number of features and capabilities that help IT administrators manage and protect devices, deploy and manage applications, enforce security policies, and ensure compliance within their organization. Intune's key features include:

* Device Management
* Application Management:
* Data Protection:
* Compliance and Security:

Intune provides organizations with greater flexibility, scalability, and ease of use by providing a unified and cloud-native approach to managing and securing devices and applications. It works well with other Microsoft solutions and services, such as Azure Active Directory and Microsoft 365, to provide an all-encompassing endpoint management and security solution.

With Intune, organizations can use a centralized and cloud-based management console to implement modern management practices, empower their workforce to be productive on any device, and ensure the security and compliance of their digital assets.

Intune supports a variety of application deployment methods, but for the purposes of this book, we will focus on LOB (line of business) and Win32\. Let's look at how these two deployment methods compare in Intune.

Looking at LOB (Line of Business) Applications, we can see the following conditions::

* LOB applications are typically custom-built or specialized applications that an organization develops in-house to meet their specific business needs.
* Deploying LOB applications entails directly uploading the application package (e.g.,.appx,.msi) to Intune. After that, the package is distributed and installed on managed devices.
* LOB applications are primarily designed for modern platforms such as Windows 10 and later, but they may also support other platforms such as iOS and Android.
* LOB applications are ideal for deploying custom or business-specific applications within a company. They are frequently organization-specific and may not be available in public app stores.
* Intune offers LOB application management capabilities such as app installation, updates, and removal, as well as the ability to enforce policies and configurations specific to these applications.
* For LOB applications to be deployed, the application package must be available for upload, as well as proper signing certificates and relevant metadata.

Win32 Applications, on the other hand, are intended for a variety of purposes.:

* Win32 applications are traditional desktop applications that were not created with modern management platforms in mind.
* The Intune Win32 App Packaging Tool is used to create an application package for Win32 application deployment. The application installer (e.g.,.exe), installation script, and other dependencies are typically included in the package. The package is distributed and installed on managed devices via Intune.
* Win32 applications work with a variety of Windows versions, including legacy Windows 7 and Windows 8.1, 10, as well as modern Windows 11.
* Win32 applications are appropriate for deploying traditional desktop applications, such as legacy or complex applications that may necessitate customization or special installation procedures.
* Intune provides Win32 application management capabilities such as app installation, updates, removal, and policy enforcement. Furthermore, Win32 applications can use detection rules to determine whether or not the application is already installed on the device.
* Converting the application installer into a format compatible with Intune, as well as relevant configuration files and detection rules, is required when creating a Win32 application package.

In summary, LOB applications are organization-specific applications, whereas Win32 applications are traditional desktop applications. LOB applications are typically designed for modern platforms, whereas Win32 applications are more universal. Both deployment methods offer management capabilities, but the packaging and deployment processes vary depending on the application. Depending on the application requirements and compatibility with the target devices and platforms, organizations can select the best deployment method.

To make it easier to understand the difference between the two, we can look at LOB applications somewhat as MSI deployments with SCCM and Win32 deployments are similar to Script installations in SCCM. Of course you need to take in consideration multiple factors when creating such applications and for now, the business standard usually leans to Win32 deployments. For now, let’s take a look at how to deploy you application with both methods.

### Deploy MSI via LOBA

Deploying an MSI with LOB (Line of Business) applications in Intune involves a few steps. Here is a step-by-step guide to help you deploy an MSI using the LOB method in Intune:

Step 1: Prepare the MSI Package

Of course the first step is to create and prepare the MSI package with all the necessary configurations and adjustments before deploying it. In our case we will use the repackaged VLC Media Player MSI.

Step 2: Upload the MSI to Intune

\- Sign in to the[Microsoft Endpoint Manager admin center](https://endpoint.microsoft.com/ "Microsoft Endpoint Manager admin center") with your Intune administrator credentials.

![intune mem admin center front page](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-front-page.png "intune mem admin center front page")  

\- Navigate to "Apps" > "All apps." Click on "Add" to add a new app.

![intune mem admin center add app](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-add-app.png "intune mem admin center add app")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2037334/7443" target="_top" id="2037334">
  <img src="//a.impactradius-go.com/display-ad/7443-2037334" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2037334/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- Select "Line-of-business app" as the app type.

![intune mem admin center loba select](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-loba-select.png "intune mem admin center loba select")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2049390/7443" target="_top" id="2049390">
  <img src="//a.impactradius-go.com/display-ad/7443-2049390" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2049390/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- Select the App Package File

![intune mem admin center loba app package](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-loba-app-package.png "intune mem admin center loba app package")  

Step 3: Configure the App Details

\- Provide the necessary details, such as the app name, description, and publisher information.

![intune mem admin center loba app details](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-loba-app-details.png "intune mem admin center loba app details")  

As you can see, just as the case with deploying MSI packages with SCCM, no detection method is requested because Intune automatically picks up the Product Code of the MSI package and uses it as a detection to check if the application has been successfully installed on the target devices/users.

Step 4: Assign the App to Groups

\- Click on "Assignments" to assign the app to specific user groups or device groups and choose the appropriate groups based on your deployment requirements.

![intune mem admin center loba app assign](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-loba-app-assign.png "intune mem admin center loba app assign")  

Step 5: Review and Deploy the App

\- Review the app settings and ensure everything is configured correctly. If everything is correct click on Create.

![intune mem admin center loba app review create](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-loba-app-review-create.png "intune mem admin center loba app review create")  

### Deploy EXE/VBScript/PowerShell via Win32

Deploying EXE installers, VBScript or PowerShell wrappers via the Win32 method requires more steps with Intune as it requires more steps with SCCM, so let’s take a look at what is necessary to create and deploy a Win32 Application.

Let us assume that we have created a PowerShell wrapper for our VLC Media Player repackaged application with [PSADT](https://psappdeploytoolkit.com/ "PSADT").

Step 1: Prepare the PowerShell Script

Create or obtain the PowerShell script that you want to deploy. Ensure that the script performs the desired actions and is compatible with the target devices and platforms. We won’t go through all the steps on creating and modifying the PSADT template in this example. For more information c[heck out our first MSI Packaging Ebook](https://tools.techidaily.com/advancedinstaller/products/).

![psadt create script](https://cdn.advancedinstaller.com/img/intune-package-deployment/psadt-create-script.png "psadt create script")  

Step 2: Package the PowerShell Script

When it comes to Win32 applications in Intune, you can’t just upload the source media as it is and this must be converted to an .intunewin format using the [Microsoft Win32 Content Prep Tool](https://github.com/microsoft/Microsoft-Win32-Content-Prep-Tool "Microsoft Win32 Content Prep Tool"). The Microsoft Win32 Content Prep Tool is a command-line utility provided by Microsoft that assists in the preparation of Win32 app packages for deployment via Microsoft Endpoint Manager (formerly known as Microsoft Intune). It is intended to streamline the packaging process and ensure that Win32 app packages meet the requirements for enterprise deployment.

First, download the tool from the oficial Github repository. Once the tool is downloaded, extract it from the zip file. Next, open up a command prompt and use the following command:

IntuneWinAppUtil -c <setup_folder> -s <source_setup_file> -o <output_folder> <-q>

Copy

The.intunewin file will be generated from the specified source folder and setup file.This tool will retrieve the necessary information for Intune from an MSI setup file.If the -a option is used, all catalog files in that folder are bundled into the.intunewin file.It will be in quiet mode if -q is specified. The output file will be overwritten if it already exists.In addition, if the output folder does not already exist, it will be created.

![win32 content prep tool](https://cdn.advancedinstaller.com/img/intune-package-deployment/win32-content-prep-tool.png "win32 content prep tool")  

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)The Microsoft Win32 Content Prep Tool does not have a GUI, but if you want one you can download the [IntuneWinAppUtil GUI utility for free](https://www.alexandrumarin.com/downloads/ "IntuneWinAppUtil GUI utility for free").

Once the conversion is successful, the output folder should contain the .intunewin file necessary to upload to Intune.

![win32 content prep tool output](https://cdn.advancedinstaller.com/img/intune-package-deployment/win32-content-prep-tool-output.png "win32 content prep tool output")  

Step 3: Create the Intune Win32 App Package

\- Sign in to the[Microsoft Endpoint Manager admin center](https://endpoint.microsoft.com/ "Microsoft Endpoint Manager admin center") with your Intune administrator credentials.

![intune mem admin center front page](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-front-page.png "intune mem admin center front page")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2094415/7443" target="_top" id="2094415">
  <img src="//a.impactradius-go.com/display-ad/7443-2094415" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2094415/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- Navigate to "Apps" > "All apps." Click on "Add" to add a new app.

![intune mem admin center add app](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-add-app.png "intune mem admin center add app")  

\- Select "Windows app (Win32)" as the app type.

![intune mem admin center win32 select](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-win32-select.png "intune mem admin center win32 select")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2118323/7443" target="_top" id="2118323">
  <img src="//a.impactradius-go.com/display-ad/7443-2118323" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2118323/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- Select the App Package File, in our case the .intunewin file created earlier

![intune mem admin center win32 app package](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-win32-app-package.png "intune mem admin center win32 app package")  

<!-- affiliate ads begin -->
<span id="1983474">
					<video width="576" height="240" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1983474.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/22993-1983474">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1983474.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:360px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fhomestyler.sjv.io%2Fc%2F5597632%2F1983474%2F22993'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1983474/22993" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Step 4: Configure the App Details

\- Provide the necessary details, such as the app name, description, and publisher information 

![intune mem admin center win32 app details](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-win32-app-details.png "intune mem admin center win32 app details")  

Step 5: Define the Installation parameters and behaviors

\- Fill in other relevant information, such as the installation command and uninstall command. Most of the behavior is similar to SCCM methods

![intune mem admin center win32 app install](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-win32-app-install.png "intune mem admin center win32 app install")  

Step 6: Define Application Requirements

\- Specify any requirements or dependencies for the app, such as minimum operating system versions or device architectures.

![intune mem admin center win32 app requirements](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-win32-app-requirements.png "intune mem admin center win32 app requirements")  

Step 7: Define the Detection Method

\- Specify the detection method for the app, which determines whether the app is already installed on the target device. Because we have an MSI we can still use the Product Code of our MSI as a detection method

![intune mem admin center win32 app detection](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-win32-app-detection.png "intune mem admin center win32 app detection")  

Step 8: Configure Dependencies

\- If required, add any dependencies to ensure the app is deployed correctly

![intune mem admin center win32 app dependencies](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-win32-app-dependencies.png "intune mem admin center win32 app dependencies")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2123750/7443" target="_top" id="2123750">
  <img src="//a.impactradius-go.com/display-ad/7443-2123750" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2123750/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Step 9: Configure Supersedence

Supersedence in Intune apps refers to the ability to replace or upgrade an existing deployed application with a newer version. It allows you to manage the lifecycle of applications by automatically detecting and handling updates or upgrades to applications in your environment.

When an application is superseded, it means that a new version of the application is available, and Intune will handle the process of replacing the older version with the new one on targeted devices. Supersedence helps ensure that devices stay up to date with the latest versions of applications, providing improved functionality, security updates, and bug fixes.

![intune mem admin center win32 app supersedence](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-win32-app-supersedence.png "intune mem admin center win32 app supersedence")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2082542/7443" target="_top" id="2082542">
  <img src="//a.impactradius-go.com/display-ad/7443-2082542" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2082542/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Step 10: Assign the App to Groups

\- Click on "Assignments" to assign the app to specific user groups or device groups and select the appropriate groups based on your deployment requirements.

![intune mem admin center win32 app assign](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-win32-app-assign.png "intune mem admin center win32 app assign")  

<!-- affiliate ads begin -->
<a href="https://unicoeye.pxf.io/c/5597632/2148775/18498" target="_top" id="2148775">
  <img src="//a.impactradius-go.com/display-ad/18498-2148775" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://unicoeye.pxf.io/i/5597632/2148775/18498" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Step 8: Review and Deploy the App

Review the app settings and ensure everything is configured correctly. If everything is correct click on Create.

![intune mem admin center win32 app create](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-win32-app-create.png "intune mem admin center win32 app create")  

As you can see, the Win32 deployments are more lengthy and require more steps, but if you look closely it gives you a more granular view and control of your application deployment, hence why this method has been widely adopted by the IT Professionals.

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
<li><a href="https://facebook-video-footage.techidaily.com/updated-high-quality-game-capture-apps-reviewed/"><u>[Updated] High-Quality Game Capture Apps Reviewed</u></a></li>
<li><a href="https://twitter-videos.techidaily.com/updated-streamline-and-stand-out-twitters-video-directive-for-2024/"><u>[Updated] Streamline and Stand Out Twitter's Video Directive for 2024</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/best-5-ways-to-enhance-your-videos-with-60fps-conversion-techniques/"><u>Best 5 Ways to Enhance Your Videos with 60Fps Conversion Techniques</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/comprehensive-guide-understanding-the-wma-audio-file-format/"><u>Comprehensive Guide: Understanding the WMA Audio File Format</u></a></li>
<li><a href="https://android-location.techidaily.com/easy-ways-to-manage-your-xiaomi-redmi-note-13-pro-5g-location-settings-drfone-by-drfone-virtual/"><u>Easy Ways to Manage Your Xiaomi Redmi Note 13 Pro 5G Location Settings | Dr.fone</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/effective-guide-mastering-data-restoration-with-apowerrecover/"><u>Effective Guide: Mastering Data Restoration with ApowerRecover</u></a></li>
<li><a href="https://location-social.techidaily.com/how-to-activate-and-use-life360-ghost-mode-on-nokia-105-classic-drfone-by-drfone-virtual-android/"><u>How To Activate and Use Life360 Ghost Mode On Nokia 105 Classic | Dr.fone</u></a></li>
<li><a href="https://apple-account.techidaily.com/how-to-fix-locked-apple-id-on-apple-iphone-x-by-drfone-ios/"><u>How to Fix Locked Apple ID on Apple iPhone X</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/how-to-restore-lost-videos-on-your-ipad/"><u>How To Restore Lost Videos On Your iPad</u></a></li>
<li><a href="https://some-knowledge.techidaily.com/in-2024-exclusive-guide-to-audio-alchemy-sites/"><u>In 2024, Exclusive Guide to Audio Alchemy Sites</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/mirror-your-iphone-screen-on-vizio-television-step-by-step-guide/"><u>Mirror Your iPhone Screen on Vizio Television - Step-by-Step Guide</u></a></li>
<li><a href="https://win-blog.techidaily.com/overcoming-continuous-launch-glitches-in-anthem-game/"><u>Overcoming Continuous Launch Glitches in Anthem Game</u></a></li>
<li><a href="https://win11-tips.techidaily.com/pathways-to-the-system32-folder-in-win11/"><u>Pathways to the System32 Folder in Win11</u></a></li>
<li><a href="https://sound-issues.techidaily.com/restoring-audio-functionality-on-mac-computers-expert-tips-and-fixes/"><u>Restoring Audio Functionality on Mac Computers: Expert Tips & Fixes</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/step-by-step-guide-separating-audios-into-individual-tracks-from-a-single-source/"><u>Step-by-Step Guide: Separating Audios Into Individual Tracks From a Single Source</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/stream-like-a-pro-ultimate-tips-for-hosting-lol-wild-rift-tournaments-on-windows-computers/"><u>Stream Like a Pro: Ultimate Tips for Hosting LoL: Wild Rift Tournaments on Windows Computers</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/ultimate-guide-how-to-safely-download-songs-from-saavn/"><u>Ultimate Guide: How to Safely Download Songs From Saavn</u></a></li>
</ul></div>

