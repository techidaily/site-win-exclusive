---
title: "Comparative Techniques in Software Remastering: Insights Into MSI and EXE Conversion Strategies"
date: 2024-10-06T18:56:20.556Z
updated: 2024-10-10T20:09:38.855Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: "This Article Describes Comparative Techniques in Software Remastering: Insights Into MSI and EXE Conversion Strategies"
thumbnail: https://thmb.techidaily.com/3299531766a0d348d78dd04349d2683155a00d71b7ac283c24ce186055580244.jpg
---

## Comparative Techniques in Software Remastering: Insights Into MSI and EXE Conversion Strategies

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Way forward for your installer

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2043603/7443" target="_top" id="2043603">
  <img src="//a.impactradius-go.com/display-ad/7443-2043603" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2043603/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Strategies for Repackaging Applications: MSI and EXE Approaches

Depending on the situation, there are a number of actions you can take when it comes to repackaging an application:

* **MSI**: If the application comes as an MSI, the way forward to further customize and deploy the application would be to create transform files (MST)
* **EXE**: There are three possibilities on how to advance with an EXE installer. The most popular one is to repackage it via the snapshot method, but there are cases where the EXE installer actually contains an embedded MSI which is extracted and then installed, and the final case is where the application is so complex that it’s best to install it silently via a wrapper method

The MSI scenario is quite straightforward so we would go ahead and have a look over the EXE scenario.

The first step is to determine whether the EXE requires repackaging or if it contains an embedded MSI. There are several ways to determine whether an EXE installer contains an embedded MSI:

* Open Task Manager and check if the msiexec service appears in the list during the installation
* Check the [Uninstall registry](https://tools.techidaily.com/advancedinstaller/products/) and see what uninstall command has appeared or if the key name resembles an MSI Product Code
* Use [Process Monitor](https://learn.microsoft.com/en-us/sysinternals/downloads/procmon "Process Monitor")

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2111994/7443" target="_top" id="2111994">
  <img src="//a.impactradius-go.com/display-ad/7443-2111994" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2111994/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Using Process Monitor to Detect embedded MSI in EXE

Process Monitor has grown in popularity among IT professionals for not only detecting whether an MSI is embedded in another MSI, but also for detecting additional system changes performed by applications, debugging applications, and so on.

To detect if an EXE contains an embedded MSI with Process Monitor, follow these steps:

\- DownloadProcess Monitor: Visit the official website of Process Monitor (<https://learn.microsoft.com/en-us/sysinternals/downloads/procmon>) and download the latest version of the tool. 

\- Launch Process Monitor: Extract the archive and start Process Monitor

\- Configure filters: Before monitoring the installation process, it's helpful to set up filters to narrow down the captured events and focus on the relevant activities. Click on the "Filter" menu, and then select "Filter..." to open the Filter dialog box.

![process monitor filters window](https://cdn.advancedinstaller.com/img/repackaging-action-steps/process-monitor-filters-window.png "process monitor filters window")  

<!-- affiliate ads begin -->
<span id="1983473">
					<video width="576" height="240" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1983473.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/22993-1983473">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1983473.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:360px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fhomestyler.sjv.io%2Fc%2F5597632%2F1983473%2F22993'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1983473/22993" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- Configure filter rules: In the Filter dialog box, specify the conditions to filter the events. To detect if an EXE installer contains an embedded MSI, you can set up the following filters: In the "Display entries matching these conditions" select "Operation", “is”, “Process Create” and then “include’. Click on Add.

![process monitor operation is process create](https://cdn.advancedinstaller.com/img/repackaging-action-steps/process-monitor-operation-is-process-create.png "process monitor operation is process create")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2129738/7443" target="_top" id="2129738">
  <img src="//a.impactradius-go.com/display-ad/7443-2129738" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2129738/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- These filters will record events related to the EXE installer and any MSI files used during its execution.

\- Begin capturing events: After configuring the filters, select "Start" from the "Capture" menu, or press the Ctrl + E shortcut to begin capturing events.

\- Run the EXE installer: Launch the EXE installer you want to analyze. The Process Monitor will start capturing events in real-time.

\- Analyze captured events: When the installation is finished, or when you want to stop capturing events, go to the "Capture" menu and select "Stop," or press the Ctrl + E shortcut. In the main window of Process Monitor, a list of captured events will be displayed.

\- Filter and analyze events: To analyze the captured events, use the various columns and filter options in the Process Monitor window. Look for file system operations involving MSI files (with the extension ".msi") and registry operations involving MSI execution (ending with ".msiexec.exe"). These events indicate that an MSI is embedded within the EXE installer.

For example, if we install Tableau Reader and start the Process Monitor tool and follow the above steps, we will have the following operations captured:

![process monitor detect msi](https://cdn.advancedinstaller.com/img/repackaging-action-steps/process-monitor-detect-msi.png "process monitor detect msi")  

We're most interested in the Path and Detail columns. Looking at what TableauReader.exe does, it first extracts the installer data into a temporary directory in the %temp% directory, then installs the Visual C++ Redistributables 2013, followed by the Tableau Reader. However, if we look closely, we can see that the msiexec.exe service is called, indicating that the exe file is extracting the file in that %temp% location.

This is an example where you will need to create a transform file (MST) to further customize the Tableau Reader MSI installation, but also to use the [dependencies](https://tools.techidaily.com/advancedinstaller/products/) to declare that Visual C++ Redistributable 2013 is needed in order for the application to function properly.

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
<li><a href="https://extra-support.techidaily.com/new-perfecting-iphone-images-in-dim-light/"><u>[New] Perfecting iPhone Images in Dim Light</u></a></li>
<li><a href="https://fox-direct.techidaily.com/updated-plex-media-player-centralized-home-entertainment/"><u>[Updated] Plex Media Player Centralized Home Entertainment</u></a></li>
<li><a href="https://instagram-video-files.techidaily.com/updated-precision-polling-on-instagram-crafting-survey-content/"><u>[Updated] Precision Polling on Instagram Crafting Survey Content</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/1-simplify-your-channel-top-strategies-for-free-youtube-video-compression/"><u>1. Simplify Your Channel: Top Strategies for Free YouTube Video Compression</u></a></li>
<li><a href="https://youtube-zero.techidaily.com/approved-green-screen-mastery-on-youtube-ideas-unleashed/"><u>2024 Approved Green Screen Mastery on YouTube - Ideas Unleashed</u></a></li>
<li><a href="https://fox-access.techidaily.com/2024-approved-virtual-enterprise-integrating-vr-tech-in-commerce/"><u>2024 Approved Virtual Enterprise Integrating VR Tech in Commerce</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/comprehensive-guide-adding-and-deleting-assemblies-with-custom-actions-for-enhanced-functionality/"><u>Comprehensive Guide: Adding and Deleting Assemblies with Custom Actions for Enhanced Functionality</u></a></li>
<li><a href="https://smart-video-creator.techidaily.com/free-dvd-playback-on-windows-10-our-top-10-recommendations/"><u>Free DVD Playback on Windows 10 Our Top 10 Recommendations</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/guide-to-delivering-software-through-sccm-msi-exe-vbscript-and-powershell-techniques/"><u>Guide to Delivering Software Through SCCM: MSI, EXE, VBScript & PowerShell Techniques</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/successful-strategies-for-broadcasting-yourself-live-a-comprehensive-guide/"><u>Successful Strategies for Broadcasting Yourself Live: A Comprehensive Guide</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/top-5-tips-for-effortless-recording-of-your-telegram-video-meetings/"><u>Top 5 Tips for Effortless Recording of Your Telegram Video Meetings</u></a></li>
<li><a href="https://win-able.techidaily.com/troubleshoot-and-tame-six-ways-to-minimize-zooms-cpu-demands/"><u>Troubleshoot and Tame: Six Ways to Minimize Zoom's CPU Demands</u></a></li>
</ul></div>

