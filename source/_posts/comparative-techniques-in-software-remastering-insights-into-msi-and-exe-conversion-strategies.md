---
title: "Comparative Techniques in Software Remastering: Insights Into MSI and EXE Conversion Strategies"
date: 2024-10-04T17:07:29.798Z
updated: 2024-10-05T19:16:27.211Z
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
<a href="https://bluettius.sjv.io/c/5597632/2139117/17108" target="_top" id="2139117">
  <img src="//a.impactradius-go.com/display-ad/17108-2139117" border="0" alt="https://techidaily.com" width="320" height="90"/>
</a>
<img height="0" width="0" src="https://bluettius.sjv.io/i/5597632/2139117/17108" style="position:absolute;visibility:hidden;" border="0" />
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
<a href="https://appsumo.8odi.net/c/5597632/2151868/7443" target="_top" id="2151868">
  <img src="//a.impactradius-go.com/display-ad/7443-2151868" border="0" alt="https://techidaily.com" width="600" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2151868/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Using Process Monitor to Detect embedded MSI in EXE

Process Monitor has grown in popularity among IT professionals for not only detecting whether an MSI is embedded in another MSI, but also for detecting additional system changes performed by applications, debugging applications, and so on.

To detect if an EXE contains an embedded MSI with Process Monitor, follow these steps:

\- DownloadProcess Monitor: Visit the official website of Process Monitor (<https://learn.microsoft.com/en-us/sysinternals/downloads/procmon>) and download the latest version of the tool. 

\- Launch Process Monitor: Extract the archive and start Process Monitor

\- Configure filters: Before monitoring the installation process, it's helpful to set up filters to narrow down the captured events and focus on the relevant activities. Click on the "Filter" menu, and then select "Filter..." to open the Filter dialog box.

![process monitor filters window](https://cdn.advancedinstaller.com/img/repackaging-action-steps/process-monitor-filters-window.png "process monitor filters window")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1997717/19272" target="_top" id="1997717">
  <img src="//a.impactradius-go.com/display-ad/19272-1997717" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1997717/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- Configure filter rules: In the Filter dialog box, specify the conditions to filter the events. To detect if an EXE installer contains an embedded MSI, you can set up the following filters: In the "Display entries matching these conditions" select "Operation", “is”, “Process Create” and then “include’. Click on Add.

![process monitor operation is process create](https://cdn.advancedinstaller.com/img/repackaging-action-steps/process-monitor-operation-is-process-create.png "process monitor operation is process create")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2130890/7443" target="_top" id="2130890">
  <img src="//a.impactradius-go.com/display-ad/7443-2130890" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2130890/7443" style="position:absolute;visibility:hidden;" border="0" />
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
<li><a href="https://some-skills.techidaily.com/updated-transforming-traditional-markets-with-virtual-engineering/"><u>[Updated] Transforming Traditional Markets with Virtual Engineering</u></a></li>
<li><a href="https://location-fake.techidaily.com/8-solutions-to-fix-find-my-friends-location-not-available-on-realme-c33-2023-drfone-by-drfone-virtual-android/"><u>8 Solutions to Fix Find My Friends Location Not Available On Realme C33 2023 | Dr.fone</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/best-free-pdf-editing-software-optimal-choice-for-windows-11-users/"><u>Best Free PDF Editing Software: Optimal Choice for Windows 11 Users</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/best-tools-and-websites-to-download-mp3-from-youtube-videos/"><u>Best Tools and Websites to Download MP3 From YouTube Videos</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/building-a-safe-digital-environment-incorporating-anti-money-laundering-measures-in-banking-software/"><u>Building a Safe Digital Environment: Incorporating Anti-Money Laundering Measures in Banking Software</u></a></li>
<li><a href="https://win-dash.techidaily.com/download-latest-nvidia-quadro-rtx-8000-drivers-compatible-with-windows-1087/"><u>Download Latest NVIDIA Quadro RTX 8000 Drivers Compatible with Windows 10/8/7</u></a></li>
<li><a href="https://vp-tips.techidaily.com/from-hd-to-hyper-hd-the-eizo-monitor-revolution-with-cg318-4k-for-2024/"><u>From HD to Hyper HD The EIZO Monitor Revolution with CG318-4K for 2024</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/seamless-integration-transferring-your-bank-records-into-quickbooks-effortlessly/"><u>Seamless Integration: Transferring Your Bank Records Into QuickBooks Effortlessly</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/secure-your-windows-10-computer-with-an-easy-to-make-usb-safety-device/"><u>Secure Your Windows 10 Computer with an Easy-to-Make USB Safety Device</u></a></li>
<li><a href="https://program-issues.techidaily.com/steam-wont-see-my-controller-heres-the-quick-fix-for-windows-users/"><u>Steam Won't See My Controller? Here's the Quick Fix for Windows Users</u></a></li>
<li><a href="https://fox-that.techidaily.com/the-ultimate-fix-for-when-visual-look-up-wont-work-on-your-iphone/"><u>The Ultimate Fix for When Visual Look Up Won't Work on Your iPhone</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/top-11-ios-11-troubleshooting-guide-solutions-and-tips/"><u>Top 11 iOS 11 Troubleshooting Guide: Solutions & Tips</u></a></li>
<li><a href="https://program-issues.techidaily.com/1723011787866-twitch-audio-not-working-heres-how-to-fix-streaming-silence/"><u>Twitch Audio Not Working? Here's How to Fix Streaming Silence</u></a></li>
<li><a href="https://tech-recovery.techidaily.com/unlocking-the-secrets-of-the-chkdsk-command-in-windows-operating-systems/"><u>Unlocking the Secrets of the Chkdsk Command in Windows Operating Systems</u></a></li>
</ul></div>

