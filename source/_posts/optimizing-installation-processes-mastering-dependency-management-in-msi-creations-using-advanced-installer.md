---
title: "Optimizing Installation Processes: Mastering Dependency Management in MSI Creations Using Advanced Installer"
date: 2024-10-03T18:23:40.109Z
updated: 2024-10-10T16:05:32.798Z
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
<a href="https://unicoeye.pxf.io/c/5597632/2134495/18498" target="_top" id="2134495">
  <img src="//a.impactradius-go.com/display-ad/18498-2134495" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://unicoeye.pxf.io/i/5597632/2134495/18498" style="position:absolute;visibility:hidden;" border="0" />
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

<!-- affiliate ads begin -->
<span id="1304647">
					<video width="240" height="200" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1304647.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/15852-1304647">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1304647.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:150px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fthefitville.pxf.io%2Fc%2F5597632%2F1304647%2F15852'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1304647/15852" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

You can also select the extract folder for each selected prerequisite, keep the prerequisite files after installation, hide installed prerequisites and check the launch conditions before searching for the prerequisites.

### How to Enable Windows Features with Advanced Installer

Advanced Installer also allows you to enable Windows Features.Some Windows programs and features must be enabled before applications can use them. Other features are enabled by default, but you can disable them if your application does not require them.

Use the \[Windows Feature bundle\] toolbar button or the "New Windows Feature bundle" context menu item to add a Windows Features bundle then select the Target Operating System. Once you have chosen the OS, the Available Windows Features will be populated with all the options available for those particular OSes.

![ai prerequisites windows features](https://cdn.advancedinstaller.com/img/adding-prerequisites-to-packages/ai-prerequisites-windows-features.png "ai prerequisites windows features")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2068439/7443" target="_top" id="2068439">
  <img src="//a.impactradius-go.com/display-ad/7443-2068439" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2068439/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Advanced Installer also offers multiple Windows Server roles from which you can choose to include in your package. Roles selected in this view only apply when running the package on a Windows Server. They will be ignored on any other OS type.

To include a server role in your package, select the Windows Server Roles tree item, then check the roles you want to include. The roles are organized by the earliest supported version of the target server's operating system.

![ai prerequisites windows server roles](https://cdn.advancedinstaller.com/img/adding-prerequisites-to-packages/ai-prerequisites-windows-server-roles.png "ai prerequisites windows server roles")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2082520/7443" target="_top" id="2082520">
  <img src="//a.impactradius-go.com/display-ad/7443-2082520" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2082520/7443" style="position:absolute;visibility:hidden;" border="0" />
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
<li><a href="https://fox-blue.techidaily.com/updated-in-2024-ideal-images-scenery-for-engaging-online-audiences/"><u>[Updated] In 2024, Ideal Images Scenery for Engaging Online Audiences</u></a></li>
<li><a href="https://extra-approaches.techidaily.com/updated-perfecting-your-youtube-experience-stop-previews/"><u>[Updated] Perfecting Your YouTube Experience - Stop Previews</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/1-top-ranking-video-introduction-creators-for-your-blog-or-channel/"><u>1. Top-Ranking Video Introduction Creators for Your Blog or Channel</u></a></li>
<li><a href="https://facebook-video-content.techidaily.com/2024-approved-decoding-the-process-of-capturing-facebooks-gifs-on-mobilepc/"><u>2024 Approved Decoding the Process of Capturing Facebook's GIFs on Mobile/PC</u></a></li>
<li><a href="https://some-skills.techidaily.com/2024-approved-interpreting-differences-360-and-virtual-reality-cinematography/"><u>2024 Approved Interpreting Differences 360° and Virtual Reality Cinematography</u></a></li>
<li><a href="https://youtube-help.techidaily.com/2024-approved-premium-screener-tech-perfect-for-youtube-videos/"><u>2024 Approved Premium Screener Tech Perfect for YouTube Videos</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/beginners-tutorial-adding-and-modifying-pictures-within-a-pdf-file/"><u>Beginner's Tutorial: Adding and Modifying Pictures Within a PDF File</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/bridging-windows-11-with-your-tv-screen-the-ultimate-how-to-guide/"><u>Bridging Windows 11 with Your TV Screen: The Ultimate How-To Guide</u></a></li>
<li><a href="https://screen-sharing-recording.techidaily.com/captureit-all-revisiting-recordmax-users-for-2024/"><u>CaptureIt All! Revisiting 'RecordMax' Users for 2024</u></a></li>
<li><a href="https://screen-activity-recording.techidaily.com/fives-finest-time-lapse-capture-apps-reviewed-for-2024/"><u>Five's Finest Time-Lapse Capture Apps Reviewed for 2024</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/how-to-efficiently-convert-wmv-videos-into-high-quality-mp4-players/"><u>How to Efficiently Convert WMV Videos Into High-Quality MP4 Players</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/simplifying-file-conversion-mastering-powershell-and-vbscript-for-efficient-de-hardening/"><u>Simplifying File Conversion: Mastering PowerShell & VBScript for Efficient De-Hardening</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/step-by-step-guide-to-shifting-images-from-an-iphone-onto-a-samsung-galaxy-s10-smartphone/"><u>Step-by-Step Guide to Shifting Images From an iPhone Onto a Samsung Galaxy S10 Smartphone</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/top-11-ios-11-troubleshooting-guide-solutions-and-tips/"><u>Top 11 iOS 11 Troubleshooting Guide: Solutions & Tips</u></a></li>
<li><a href="https://fox-tls.techidaily.com/unmasking-the-invisible-effective-strategies-for-identifying-espionage-software-on-android-phones/"><u>Unmasking the Invisible: Effective Strategies for Identifying Espionage Software on Android Phones</u></a></li>
</ul></div>

