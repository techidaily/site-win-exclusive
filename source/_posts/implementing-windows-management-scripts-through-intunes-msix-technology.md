---
title: Implementing Windows Management Scripts Through Intune's MSIX Technology
date: 2024-09-26T00:01:54.517Z
updated: 2024-09-29T17:47:42.961Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: This Article Describes Implementing Windows Management Scripts Through Intune's MSIX Technology
thumbnail: https://thmb.techidaily.com/a1972899444c7fd6c447adfaf7d10b9ab8c7ebd024be2fc74b2760fa4d84aacb.jpg
---

## Implementing Windows Management Scripts Through Intune's MSIX Technology

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

<!-- affiliate ads begin -->
<a href="https://laganoo.pxf.io/c/5597632/1528700/16446" target="_top" id="1528700">
  <img src="//a.impactradius-go.com/display-ad/16446-1528700" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://laganoo.pxf.io/i/5597632/1528700/16446" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- Navigate to "Apps" > "All apps." Click on "Add" to add a new app.

![intune mem admin center add app](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-add-app.png "intune mem admin center add app")  

\- Select "Line-of-business app" as the app type.

![intune mem admin center loba select](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-loba-select.png "intune mem admin center loba select")  

\- Select the App Package File

![intune mem admin center loba app package](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-loba-app-package.png "intune mem admin center loba app package")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2049379/7443" target="_top" id="2049379">
  <img src="//a.impactradius-go.com/display-ad/7443-2049379" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2049379/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

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

<!-- affiliate ads begin -->
<span id="1770544">
					<video width="240" height="480" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1770544.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/20702-1770544">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1770544.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:150px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Ftokenmetrics.sjv.io%2Fc%2F5597632%2F1770544%2F20702'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1770544/20702" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

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

<!-- affiliate ads begin -->
<a href="https://unicoeye.pxf.io/c/5597632/2134239/18498" target="_top" id="2134239">
  <img src="//a.impactradius-go.com/display-ad/18498-2134239" border="0" alt="https://techidaily.com" width="721" height="90"/>
</a>
<img height="0" width="0" src="https://unicoeye.pxf.io/i/5597632/2134239/18498" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Once the conversion is successful, the output folder should contain the .intunewin file necessary to upload to Intune.

![win32 content prep tool output](https://cdn.advancedinstaller.com/img/intune-package-deployment/win32-content-prep-tool-output.png "win32 content prep tool output")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2144282/7443" target="_top" id="2144282">
  <img src="//a.impactradius-go.com/display-ad/7443-2144282" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2144282/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Step 3: Create the Intune Win32 App Package

\- Sign in to the[Microsoft Endpoint Manager admin center](https://endpoint.microsoft.com/ "Microsoft Endpoint Manager admin center") with your Intune administrator credentials.

![intune mem admin center front page](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-front-page.png "intune mem admin center front page")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2111995/7443" target="_top" id="2111995">
  <img src="//a.impactradius-go.com/display-ad/7443-2111995" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2111995/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- Navigate to "Apps" > "All apps." Click on "Add" to add a new app.

![intune mem admin center add app](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-add-app.png "intune mem admin center add app")  

\- Select "Windows app (Win32)" as the app type.

![intune mem admin center win32 select](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-win32-select.png "intune mem admin center win32 select")  

\- Select the App Package File, in our case the .intunewin file created earlier

![intune mem admin center win32 app package](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-win32-app-package.png "intune mem admin center win32 app package")  

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
<a href="https://aligracehair.sjv.io/c/5597632/1886019/19272" target="_top" id="1886019">
  <img src="//a.impactradius-go.com/display-ad/19272-1886019" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1886019/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Step 9: Configure Supersedence

Supersedence in Intune apps refers to the ability to replace or upgrade an existing deployed application with a newer version. It allows you to manage the lifecycle of applications by automatically detecting and handling updates or upgrades to applications in your environment.

When an application is superseded, it means that a new version of the application is available, and Intune will handle the process of replacing the older version with the new one on targeted devices. Supersedence helps ensure that devices stay up to date with the latest versions of applications, providing improved functionality, security updates, and bug fixes.

![intune mem admin center win32 app supersedence](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-win32-app-supersedence.png "intune mem admin center win32 app supersedence")  

Step 10: Assign the App to Groups

\- Click on "Assignments" to assign the app to specific user groups or device groups and select the appropriate groups based on your deployment requirements.

![intune mem admin center win32 app assign](https://cdn.advancedinstaller.com/img/intune-package-deployment/intune-mem-admin-center-win32-app-assign.png "intune mem admin center win32 app assign")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2135401/19272" target="_top" id="2135401">
  <img src="//a.impactradius-go.com/display-ad/19272-2135401" border="0" alt="https://techidaily.com" width="320" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2135401/19272" style="position:absolute;visibility:hidden;" border="0" />
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
<li><a href="https://instagram-video-files.techidaily.com/updated-faster-viewing-experience-for-instagram-feed/"><u>[Updated] Faster Viewing Experience for Instagram Feed</u></a></li>
<li><a href="https://instagram-video-recordings.techidaily.com/updated-in-2024-navigating-the-realm-of-sponsorships-on-instagram-influencer-edition/"><u>[Updated] In 2024, Navigating the Realm of Sponsorships on Instagram Influencer Edition</u></a></li>
<li><a href="https://on-screen-recording.techidaily.com/updated-in-2024-pro-tips-for-streaming-and-screening-netflix-on-mac/"><u>[Updated] In 2024, Pro-Tips for Streaming & Screening Netflix on Mac</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/filemaker/"><u>「音楽・動画をFileMakerで正常にインポートするための対策ガイド」</u></a></li>
<li><a href="https://fox-info.techidaily.com/2024-approved-excellence-in-endless-data-archiving-services/"><u>2024 Approved Excellence in Endless Data Archiving Services</u></a></li>
<li><a href="https://techtrends.techidaily.com/easy-connection-methods-for-ps-vr-and-your-desktop-system/"><u>Easy Connection Methods for PS VR and Your Desktop System</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/factory-or-pro-key-advantages-of-the-two-versions-of-nokia-video-converter/"><u>Factory or Pro? Key Advantages of the Two Versions of Nokia Video Converter</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/get-your-free-windows-10-movie-file-support-by-downloading-and-installing-the-mov-codec/"><u>Get Your Free Windows 10 Movie File Support by Downloading and Installing the Mov Codec!</u></a></li>
<li><a href="https://android-unlock.techidaily.com/in-2024-6-proven-ways-to-unlock-motorola-razr-40-ultra-phone-when-you-forget-the-password-by-drfone-android/"><u>In 2024, 6 Proven Ways to Unlock Motorola Razr 40 Ultra Phone When You Forget the Password</u></a></li>
<li><a href="https://article-files.techidaily.com/in-2024-become-a-skilled-concealer-of-in-game-voices-compre-points-on-altering-sounds-in-free-fire/"><u>In 2024, Become a Skilled Concealer of In-Game Voices Compre Points on Altering Sounds in Free Fire</u></a></li>
<li><a href="https://extra-approaches.techidaily.com/in-2024-revamp-chromebooks-soundscape-with-our-picks-for-web-extensions/"><u>In 2024, Revamp Chromebook's Soundscape with Our Picks for Web Extensions</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/in-depth-comparison-test-of-top-dvd-tools-wonderfox-vs-winx-which-wins/"><u>In-Depth Comparison Test of Top DVD Tools: WonderFox VS WinX - Which Wins?</u></a></li>
<li><a href="https://buynow-info.techidaily.com/in-depth-look-at-the-fujitsu-scansnap-ix1400-a-must-have-scanner-for-home-office-productivity-and-small-company-needs/"><u>In-Depth Look at the Fujitsu ScanSnap iX1400 - A Must-Have Scanner for Home Office Productivity and Small Company Needs</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/ipadvob/"><u>IPadにおけるVOB形式再生不可解決のステップバイ・ステップガイド</u></a></li>
<li><a href="https://buynow-reviews.techidaily.com/owc-mercury-pro-assessment-exceptional-durability-and-superior-speed/"><u>OWC Mercury Pro Assessment: Exceptional Durability and Superior Speed</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/pchulu-youtube/"><u>PCによるHulu映像のビデオ録画手引き - YouTubeで見る方法</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/step-by-step-strategies-for-archiving-irretrievable-tiktok-footage/"><u>Step-by-Step Strategies for Archiving Irretrievable TikTok Footage</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/top-techniques-to-stream-wma-files-on-your-android-device/"><u>Top Techniques to Stream WMA Files on Your Android Device</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/ultimate-techniques-for-ripping-burning-and-cloning-data-on-dvds-and-cds/"><u>Ultimate Techniques for Ripping, Burning & Cloning Data on DVDs and CDs</u></a></li>
</ul></div>

