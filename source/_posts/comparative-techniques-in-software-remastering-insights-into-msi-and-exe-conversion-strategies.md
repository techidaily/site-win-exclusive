---
title: "Comparative Techniques in Software Remastering: Insights Into MSI and EXE Conversion Strategies"
date: 2024-09-27T01:41:06.793Z
updated: 2024-09-29T23:45:14.157Z
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
<a href="https://appsumo.8odi.net/c/5597632/2002018/7443" target="_top" id="2002018">
  <img src="//a.impactradius-go.com/display-ad/7443-2002018" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2002018/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Using Process Monitor to Detect embedded MSI in EXE

Process Monitor has grown in popularity among IT professionals for not only detecting whether an MSI is embedded in another MSI, but also for detecting additional system changes performed by applications, debugging applications, and so on.

To detect if an EXE contains an embedded MSI with Process Monitor, follow these steps:

\- DownloadProcess Monitor: Visit the official website of Process Monitor (<https://learn.microsoft.com/en-us/sysinternals/downloads/procmon>) and download the latest version of the tool. 

\- Launch Process Monitor: Extract the archive and start Process Monitor

\- Configure filters: Before monitoring the installation process, it's helpful to set up filters to narrow down the captured events and focus on the relevant activities. Click on the "Filter" menu, and then select "Filter..." to open the Filter dialog box.

![process monitor filters window](https://cdn.advancedinstaller.com/img/repackaging-action-steps/process-monitor-filters-window.png "process monitor filters window")  

<!-- affiliate ads begin -->
<a href="https://ephamedtechinc.pxf.io/c/5597632/2137205/26400" target="_top" id="2137205">
  <img src="//a.impactradius-go.com/display-ad/26400-2137205" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://ephamedtechinc.pxf.io/i/5597632/2137205/26400" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- Configure filter rules: In the Filter dialog box, specify the conditions to filter the events. To detect if an EXE installer contains an embedded MSI, you can set up the following filters: In the "Display entries matching these conditions" select "Operation", “is”, “Process Create” and then “include’. Click on Add.

![process monitor operation is process create](https://cdn.advancedinstaller.com/img/repackaging-action-steps/process-monitor-operation-is-process-create.png "process monitor operation is process create")  

<!-- affiliate ads begin -->
<span id="1983588">
					<video width="576" height="240" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1983588.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/22993-1983588">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1983588.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:360px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fhomestyler.sjv.io%2Fc%2F5597632%2F1983588%2F22993'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1983588/22993" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- These filters will record events related to the EXE installer and any MSI files used during its execution.

\- Begin capturing events: After configuring the filters, select "Start" from the "Capture" menu, or press the Ctrl + E shortcut to begin capturing events.

\- Run the EXE installer: Launch the EXE installer you want to analyze. The Process Monitor will start capturing events in real-time.

\- Analyze captured events: When the installation is finished, or when you want to stop capturing events, go to the "Capture" menu and select "Stop," or press the Ctrl + E shortcut. In the main window of Process Monitor, a list of captured events will be displayed.

\- Filter and analyze events: To analyze the captured events, use the various columns and filter options in the Process Monitor window. Look for file system operations involving MSI files (with the extension ".msi") and registry operations involving MSI execution (ending with ".msiexec.exe"). These events indicate that an MSI is embedded within the EXE installer.

For example, if we install Tableau Reader and start the Process Monitor tool and follow the above steps, we will have the following operations captured:

![process monitor detect msi](https://cdn.advancedinstaller.com/img/repackaging-action-steps/process-monitor-detect-msi.png "process monitor detect msi")  

<!-- affiliate ads begin -->
<a href="https://aidotcom.pxf.io/c/5597632/2129042/19576" target="_top" id="2129042">
  <img src="//a.impactradius-go.com/display-ad/19576-2129042" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aidotcom.pxf.io/i/5597632/2129042/19576" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

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
<li><a href="https://video-capture.techidaily.com/updated-2024-approved-innovative-ways-to-log-ps3-competitive-sessions/"><u>[Updated] 2024 Approved Innovative Ways to Log PS3 Competitive Sessions</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/filemaker/"><u>「音楽・動画をFileMakerで正常にインポートするための対策ガイド」</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/1726029516744-chrome/"><u>Chromeビデオ再生に問題が発生したときの解決手段</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/convert-your-favorite-vimeo-videos-into-mp4-format-with-these-5-simple-cost-free-methods/"><u>Convert Your Favorite Vimeo Videos Into MP4 Format with These 5 Simple, Cost-Free Methods</u></a></li>
<li><a href="https://tech-haven.techidaily.com/easy-methods-to-perform-a-soft-reset-on-your-iphone/"><u>Easy Methods to Perform a Soft Reset on Your iPhone</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/easy-steps-to-change-trp-videos-to-ts-format-without-a-hitch/"><u>Easy Steps to Change TRP Videos to TS Format without a Hitch</u></a></li>
<li><a href="https://eaxpv-info.techidaily.com/einfachheit-perfekt-machen-einstellen-von-handbrake-fur-hevch265-kodierung/"><u>Einfachheit Perfekt Machen: Einstellen Von HandBrake Für HEVC/H.265-Kodierung</u></a></li>
<li><a href="https://win-howtos.techidaily.com/error-224003-solved-troubleshooting-non-playable-video-files/"><u>Error 224003 Solved: Troubleshooting Non-Playable Video Files</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/expert-guide-ultimate-hd-video-processing-toolkit-with-feature-rich-factory-pro-applications/"><u>Expert Guide: Ultimate HD Video Processing Toolkit with Feature-Rich Factory Pro Applications</u></a></li>
<li><a href="https://some-techniques.techidaily.com/explore-the-best-phone-options-for-enhanced-gear-vr-immersion-for-2024/"><u>Explore the Best Phone Options for Enhanced Gear VR Immersion for 2024</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/factory-or-pro-key-advantages-of-the-two-versions-of-nokia-video-converter/"><u>Factory or Pro? Key Advantages of the Two Versions of Nokia Video Converter</u></a></li>
<li><a href="https://howto.techidaily.com/fixes-for-apps-keep-crashing-on-xiaomi-redmi-note-13-pro-5g-drfone-by-drfone-fix-android-problems-fix-android-problems/"><u>Fixes for Apps Keep Crashing on Xiaomi Redmi Note 13 Pro 5G | Dr.fone</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/get-your-free-windows-10-movie-file-support-by-downloading-and-installing-the-mov-codec/"><u>Get Your Free Windows 10 Movie File Support by Downloading and Installing the Mov Codec!</u></a></li>
<li><a href="https://location-social.techidaily.com/how-to-hidefake-snapchat-location-on-your-honor-play-7t-drfone-by-drfone-virtual-android/"><u>How to Hide/Fake Snapchat Location on Your Honor Play 7T | Dr.fone</u></a></li>
<li><a href="https://activate-lock.techidaily.com/how-to-remove-activation-lock-from-the-iphone-se-without-previous-owner-by-drfone-ios/"><u>How to Remove Activation Lock From the iPhone SE Without Previous Owner?</u></a></li>
<li><a href="https://android-unlock.techidaily.com/in-2024-how-to-change-samsung-galaxy-s24-ultra-lock-screen-password-by-drfone-android/"><u>In 2024, How To Change Samsung Galaxy S24 Ultra Lock Screen Password?</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/in-depth-comparison-test-of-top-dvd-tools-wonderfox-vs-winx-which-wins/"><u>In-Depth Comparison Test of Top DVD Tools: WonderFox VS WinX - Which Wins?</u></a></li>
<li><a href="https://extra-information.techidaily.com/leverage-with-these-free-video-teasers/"><u>Leverage with These Free Video Teasers</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/1726029858827-youtubedvd/"><u>YouTube上でDVDデータを効率よくアップロードする方法説明 - ユーザーフレンドリーなチュートリアル</u></a></li>
</ul></div>

