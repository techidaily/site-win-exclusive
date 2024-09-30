---
title: "Optimizing Installation Processes: Mastering Dependency Management in MSI Creations Using Advanced Installer"
date: 2024-09-26T21:12:47.068Z
updated: 2024-09-29T23:57:22.934Z
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

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2082533/7443" target="_top" id="2082533">
  <img src="//a.impactradius-go.com/display-ad/7443-2082533" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2082533/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Prerequisites

This is where the Prerequisites feature comes in handy and lets you quickly create a bundle which contains your application and the desired dependencies.

Prerequisites are software components that must be installed before the installation of an application to ensure its proper functioning. Advanced Installer provides a wide range of prerequisites that can be easily added to MSI packages, including .NET Framework, Visual C++ Redistributable, and SQL Server Express.

Adding prerequisites to MSI packages is important for several reasons. Firstly, it ensures that the application will run correctly on target systems, reducing the risk of compatibility issues and user frustration. Secondly, it simplifies the deployment process by automating the installation of required software components. Finally, it can improve the performance of the application by ensuring that it has access to the latest software components.

Adding prerequisites with Advanced Installer is a straightforward process that can be done in just a few steps. Here's how to do it:

### Advanced Installer Prerequisites page

Open your Advanced Installer project and go to the Prerequisites page. Advanced Installer provides a wide range of options for configuring prerequisites, including the ability to specify a specific version of the prerequisite, the installation path, and the location of prerequisite files.

This view enables you to incorporate existing installers in your package, enable Windows features, and configure specific Windows Server roles.

![ai prerequisites](https://cdn.advancedinstaller.com/img/adding-prerequisites-to-packages/ai-prerequisites.png "ai prerequisites")  

<!-- affiliate ads begin -->
<a href="https://ephamedtechinc.pxf.io/c/5597632/2130533/26400" target="_top" id="2130533">
  <img src="//a.impactradius-go.com/display-ad/26400-2130533" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://ephamedtechinc.pxf.io/i/5597632/2130533/26400" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

All prerequisite setup files can be bundled with your package or placed online and accessed via a URL. If the prerequisite is not found during installation, it will be installed automatically.

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1884017/19272" target="_top" id="1884017">
  <img src="//a.impactradius-go.com/display-ad/19272-1884017" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1884017/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

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

<!-- affiliate ads begin -->
<a href="https://arkmc.pxf.io/c/5597632/352555/5172" target="_top" id="352555">
  <img src="//a.impactradius-go.com/display-ad/5172-352555" border="0" alt="https://techidaily.com" width="720" height="90"/>
</a>
<img height="0" width="0" src="https://arkmc.pxf.io/i/5597632/352555/5172" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

You can also select the extract folder for each selected prerequisite, keep the prerequisite files after installation, hide installed prerequisites and check the launch conditions before searching for the prerequisites.

### How to Enable Windows Features with Advanced Installer

Advanced Installer also allows you to enable Windows Features.Some Windows programs and features must be enabled before applications can use them. Other features are enabled by default, but you can disable them if your application does not require them.

Use the \[Windows Feature bundle\] toolbar button or the "New Windows Feature bundle" context menu item to add a Windows Features bundle then select the Target Operating System. Once you have chosen the OS, the Available Windows Features will be populated with all the options available for those particular OSes.

![ai prerequisites windows features](https://cdn.advancedinstaller.com/img/adding-prerequisites-to-packages/ai-prerequisites-windows-features.png "ai prerequisites windows features")  

Advanced Installer also offers multiple Windows Server roles from which you can choose to include in your package. Roles selected in this view only apply when running the package on a Windows Server. They will be ignored on any other OS type.

To include a server role in your package, select the Windows Server Roles tree item, then check the roles you want to include. The roles are organized by the earliest supported version of the target server's operating system.

![ai prerequisites windows server roles](https://cdn.advancedinstaller.com/img/adding-prerequisites-to-packages/ai-prerequisites-windows-server-roles.png "ai prerequisites windows server roles")  

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
<li><a href="https://youtube-blog.techidaily.com/n-2024-mastering-adsense-earnings-insights-into-payments-from-youtube-viewers/"><u>[New] In 2024, Mastering AdSense Earnings Insights Into Payments From YouTube Viewers</u></a></li>
<li><a href="https://fox-friendly.techidaily.com/updated-cutting-edge-accessories-for-gopro-devices-for-2024/"><u>[Updated] Cutting-Edge Accessories for Gopro Devices for 2024</u></a></li>
<li><a href="https://technical-tips.techidaily.com/a-comprehensive-look-at-telecommunications-companeis-and-their-services/"><u>A Comprehensive Look at Telecommunications Companeis and Their Services</u></a></li>
<li><a href="https://driver-download.techidaily.com/download-latest-amd-radeon-pro-w5700-driver-windows-11-10-and-7/"><u>Download Latest AMD Radeon Pro W5700 Driver - Windows 11, 10 & 7</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/1726027810416-flacmp3/"><u>FLAC形式へのMP3ファイル変換手順 - ステップバイステップガイド</u></a></li>
<li><a href="https://fox-cloud.techidaily.com/in-2024-expert-recommended-apps-and-sites-for-photo-frames/"><u>In 2024, Expert-Recommended Apps & Sites for Photo Frames</u></a></li>
<li><a href="https://android-frp.techidaily.com/in-2024-nubia-adb-format-tool-for-pc-vs-other-unlocking-tools-which-one-is-the-best-by-drfone-android/"><u>In 2024, Nubia ADB Format Tool for PC vs. Other Unlocking Tools Which One is the Best?</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/1726029811365-mpeg-4/"><u>MPEG-4変換手順ガイド - 動画に最適化</u></a></li>
<li><a href="https://extra-guidance.techidaily.com/revolutionary-entry-points-for-zooids-for-2024/"><u>Revolutionary Entry Points for Zooids for 2024</u></a></li>
<li><a href="https://buynow-reviews.techidaily.com/the-motorola-edgeplus-unveiled-striving-for-flagship-status-but-missing-the-mark/"><u>The Motorola Edge+ Unveiled: Striving for Flagship Status but Missing the Mark</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/win-the-new-wonderfox-collection-free-prize-and-special-deals-for-back-to-school-season-2014/"><u>Win the New WonderFox Collection – Free Prize & Special Deals for Back to School Season, 2014!</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/youtubemp3/"><u>YouTubeからMP3プレーヤーに楽曲転送テクニック</u></a></li>
</ul></div>

