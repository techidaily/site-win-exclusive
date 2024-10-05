---
title: "Optimizing Installation Processes: Mastering Dependency Management in MSI Creations Using Advanced Installer"
date: 2024-09-29T19:04:26.073Z
updated: 2024-10-05T17:18:15.259Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: "This Article Describes Optimizing Installation Processes: Mastering Dependency Management in MSI Creations Using Advanced Installer"
thumbnail: https://thmb.techidaily.com/8728071c55cb4a9d737d3c276cbce71523d45848bd43ebfc7e5000f0a5d34387.jpg
---

## Optimizing Installation Processes: Mastering Dependency Management in MSI Creations Using Advanced Installer

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Working with Dependencies

While conditional statements give you the possibility to clearly define the needed environment for your installer, it doesn’t let you modify the system in order to make the proper changes for your application to be installed. As seen in the chapter above, conditional statements for software applications can be easily added into the MSI by using Advanced Installer, but what if you want to check if that particular dependency is installed and if not, install it yourself?

### Prerequisites

This is where the Prerequisites feature comes in handy and lets you quickly create a bundle which contains your application and the desired dependencies.

Prerequisites are software components that must be installed before the installation of an application to ensure its proper functioning. Advanced Installer provides a wide range of prerequisites that can be easily added to MSI packages, including .NET Framework, Visual C++ Redistributable, and SQL Server Express.

Adding prerequisites to MSI packages is important for several reasons. Firstly, it ensures that the application will run correctly on target systems, reducing the risk of compatibility issues and user frustration. Secondly, it simplifies the deployment process by automating the installation of required software components. Finally, it can improve the performance of the application by ensuring that it has access to the latest software components.

Adding prerequisites with Advanced Installer is a straightforward process that can be done in just a few steps. Here's how to do it:

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1886003/19272" target="_top" id="1886003">
  <img src="//a.impactradius-go.com/display-ad/19272-1886003" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1886003/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Advanced Installer Prerequisites page

Open your Advanced Installer project and go to the Prerequisites page. Advanced Installer provides a wide range of options for configuring prerequisites, including the ability to specify a specific version of the prerequisite, the installation path, and the location of prerequisite files.

This view enables you to incorporate existing installers in your package, enable Windows features, and configure specific Windows Server roles.

![ai prerequisites](https://cdn.advancedinstaller.com/img/adding-prerequisites-to-packages/ai-prerequisites.png "ai prerequisites")  

All prerequisite setup files can be bundled with your package or placed online and accessed via a URL. If the prerequisite is not found during installation, it will be installed automatically.

### Download and Install Prerequisites

Advanced Installer can also download and install prerequisites from a remote location, such as a web server or network share. This ensures that the most recent versions of the prerequisite are always used, lowering the possibility of compatibility issues.

In the main Prerequisites page you can see on the right hand menu that you have a ton of predefined prerequisites that you can choose from. Some of these prerequisites are:

* .NET Framework
* .NET Core
* .NET Runtime
* SQL Server Compact
* SQL Server Express
* MySQL Server
* SQL Server OLE DB
* Adobe products
* JRE
* JDK
* Silverlight
* Python
* Internet Explorer
* DirectX
* XNA
* Access Runtimes
* Visual C++ Redistributables
* VSTO
* IIS
* Apache Tomcat
* MSML
* Windows Installer
* PowerShell
* And many more

When you select a predefined prerequisite, Advanced Installer asks you if you want to download the package next to your project and include it in the package, making the overall process much simpler.

![ai prerequisites download](https://cdn.advancedinstaller.com/img/adding-prerequisites-to-packages/ai-prerequisites-download.png "ai prerequisites download")  

You can also select the extract folder for each selected prerequisite, keep the prerequisite files after installation, hide installed prerequisites and check the launch conditions before searching for the prerequisites.

<!-- affiliate ads begin -->
<a href="https://ephamedtechinc.pxf.io/c/5597632/2130530/26400" target="_top" id="2130530">
  <img src="//a.impactradius-go.com/display-ad/26400-2130530" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://ephamedtechinc.pxf.io/i/5597632/2130530/26400" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### How to Enable Windows Features with Advanced Installer

Advanced Installer also allows you to enable Windows Features.Some Windows programs and features must be enabled before applications can use them. Other features are enabled by default, but you can disable them if your application does not require them.

Use the \[Windows Feature bundle\] toolbar button or the "New Windows Feature bundle" context menu item to add a Windows Features bundle then select the Target Operating System. Once you have chosen the OS, the Available Windows Features will be populated with all the options available for those particular OSes.

![ai prerequisites windows features](https://cdn.advancedinstaller.com/img/adding-prerequisites-to-packages/ai-prerequisites-windows-features.png "ai prerequisites windows features")  

<!-- affiliate ads begin -->
<a href="https://unicoeye.pxf.io/c/5597632/2134494/18498" target="_top" id="2134494">
  <img src="//a.impactradius-go.com/display-ad/18498-2134494" border="0" alt="https://techidaily.com" width="721" height="90"/>
</a>
<img height="0" width="0" src="https://unicoeye.pxf.io/i/5597632/2134494/18498" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Advanced Installer also offers multiple Windows Server roles from which you can choose to include in your package. Roles selected in this view only apply when running the package on a Windows Server. They will be ignored on any other OS type.

To include a server role in your package, select the Windows Server Roles tree item, then check the roles you want to include. The roles are organized by the earliest supported version of the target server's operating system.

![ai prerequisites windows server roles](https://cdn.advancedinstaller.com/img/adding-prerequisites-to-packages/ai-prerequisites-windows-server-roles.png "ai prerequisites windows server roles")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2068425/7443" target="_top" id="2068425">
  <img src="//a.impactradius-go.com/display-ad/7443-2068425" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2068425/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Of course, you can add your own packages and create a suite installation, [a chapter we have already covered in the first MSI Packaging fundamentals ebook](https://tools.techidaily.com/advancedinstaller/products/).

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
<li><a href="https://remote-screen-capture.techidaily.com/new-in-2024-document-your-days-with-xiaomis-state-of-the-art-screenshot-tool/"><u>[New] In 2024, Document Your Days with Xiaomi's State-of-the-Art Screenshot Tool</u></a></li>
<li><a href="https://some-guidance.techidaily.com/new-superior-webcams-for-professional-podcasting/"><u>[New] Superior Webcams for Professional Podcasting</u></a></li>
<li><a href="https://some-approaches.techidaily.com/2024-approved-the-essentials-of-firefoxs-pip-functionality/"><u>2024 Approved The Essentials of Firefox's PIP Functionality</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/comparing-iphone-6-and-6-plus-with-the-previous-model-iphone-5s/"><u>Comparing IPhone 6 & 6 Plus with the Previous Model: IPhone 5S</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/cutting-edge-advances-in-msi-branding-with-high-quality-packaging-options/"><u>Cutting-Edge Advances in MSI Branding with High-Quality Packaging Options</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/eradicate-the-chromium-threat-comprehensive-guide-to-cleaning-your-pc-with-malwarefox/"><u>Eradicate the Chromium Threat: Comprehensive Guide to Cleaning Your PC with MalwareFox</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/how-to-restore-lost-videos-on-your-ipad/"><u>How To Restore Lost Videos On Your iPad</u></a></li>
<li><a href="https://screen-recording.techidaily.com/in-2024-beyond-obs-streamer-friendly-broadcast-software/"><u>In 2024, Beyond OBS Streamer-Friendly Broadcast Software</u></a></li>
<li><a href="https://pokemon-go-android.techidaily.com/in-2024-can-i-use-itools-gpx-file-to-catch-the-rare-pokemon-on-honor-magic5-ultimate-drfone-by-drfone-virtual-android/"><u>In 2024, Can I use iTools gpx file to catch the rare Pokemon On Honor Magic5 Ultimate | Dr.fone</u></a></li>
<li><a href="https://some-approaches.techidaily.com/in-2024-ultimate-sd-compatibility-with-sony-a7s-ii/"><u>In 2024, Ultimate SD Compatibility with Sony A7S II</u></a></li>
<li><a href="https://fox-boxes.techidaily.com/in-2024-unleashing-potential-a-deep-dive-into-the-ion-air-pro-3-review/"><u>In 2024, Unleashing Potential A Deep Dive Into the ION Air Pro 3 Review</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/mastering-the-art-of-using-likee-a-comprehensive-guide-for-windows-users/"><u>Mastering the Art of Using Likee: A Comprehensive Guide for Windows Users</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/secure-your-computer-a-step-by-step-guide-to-using-malwarefox-for-safe-email-attachment-checks/"><u>Secure Your Computer: A Step-by-Step Guide to Using MalwareFox for Safe Email Attachment Checks</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/top-rated-iphone-passwords-apps-secure-your-data-easily/"><u>Top Rated iPhone Passwords Apps: Secure Your Data Easily</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/ultimate-guide-how-to-safely-download-songs-from-saavn/"><u>Ultimate Guide: How to Safely Download Songs From Saavn</u></a></li>
<li><a href="https://facebook-video-content.techidaily.com/uniting-viewers-facebook-live-on-the-big-screen/"><u>Uniting Viewers Facebook Live on the Big Screen</u></a></li>
<li><a href="https://audio-shaping.techidaily.com/updated-2024-approved-syncopation-spotlight-the-top-video-editing-software-for-pairing-sound-and-visuals/"><u>Updated 2024 Approved Syncopation Spotlight The Top Video Editing Software for Pairing Sound and Visuals</u></a></li>
</ul></div>

