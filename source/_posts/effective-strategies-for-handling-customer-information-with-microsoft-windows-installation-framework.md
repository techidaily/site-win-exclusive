---
title: Effective Strategies for Handling Customer Information with Microsoft Windows Installation Framework
date: 2024-10-09T16:49:47.246Z
updated: 2024-10-10T17:25:03.403Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: This Article Describes Effective Strategies for Handling Customer Information with Microsoft Windows Installation Framework
thumbnail: https://thmb.techidaily.com/c9271a8faf33c0a549b22ca0028cd9619d63965df7208919633e76ad2ce6d7e3.jpg
---

## Effective Strategies for Handling Customer Information with Microsoft Windows Installation Framework

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Best practices for user data

Because of the way MSI packages are cached in the OS once they are installed, the above solution may not be the best suited to cover all cases when it comes to user data in the form of files.

If you've ever looked through your Windows system directory, you might have noticed a folder called "Installer" in the C:Windows directory. This folder, which is frequently overlooked, plays an important role in Windows Installer technology by storing cached copies of MSI files.

The cached MSI files in the C:\\Windows\\Installer folder serve several important purposes:

* Repair and Maintenance: When an installed application has problems or becomes corrupted, Windows Installer uses the cached MSI files to repair it. This ensures the application's proper operation by restoring missing or damaged files.
* Uninstallation: The cached MSI files are used to completely remove the application from the system during the uninstallation process. To reverse the installation and remove all associated components, Windows Installer accesses the original installation package stored in the Installer folder.
* Patching: When updating or patching an installed application, Windows Installer uses the cached MSI files to identify the installed version and apply the necessary changes. Patch files, which are used for incremental updates to installed applications, are also stored in the Installer folder.

However, an MSI is not fully cached into the C:\\Windows\\Installer directory; instead, the files are removed during the caching process to save hard drive space.

If we use the above solution and delete the MSI from where it was originally installed, this operation will fail and the user will not have the VLC Media Player preferences copied in his profile when he opens the shortcut and the self-healing mechanism starts.

![vc_runtimeMinimum_x64 is missing](https://cdn.advancedinstaller.com/img/best-practices-for-user-data/vc_runtimeMinimum_x64-is-missing.png "vc_runtimeMinimum_x64 is missing")  

If the user data files are not correctly implemented, the only way for the self-healing mechanism to work is to browse to the MSI, which means copying it again on the computer.

There are several approaches we can take in this situation, but the following two will usually suffice:

* Move the files to a per-machine location and copy them to the user profile using a custom action, keep the advertised shortcuts enabled, and add a dummy registry key to HKEY CURRENT USER.
* Move the files on a per-machine location and copy them in the user profile by using a custom action, turn off the advertised shortcuts, insert the Active Setup mechanism

Both methods rely on a per-machine location for the user files and a script that copies them. Let's look at each scenario and see how we can configure it.

### Scenario one - Advertised shortcuts

We already have the advertised shortcut option on all of the shortcuts, so we'll keep it that way. Let's start with the simple part of this implementation: add a random HKEY CURRENT USER registry key if it isn't already present in the package. In our case, VLC contains the following user registry keys:

![ai vlc hkcu](https://cdn.advancedinstaller.com/img/best-practices-for-user-data/ai-vlc-hkcu.png "ai vlc hkcu")  

We need user registry keys so that the self-healing mechanism detects their absence when a user launches the shortcuts and initiates the actions. When the self-healing mechanism kicks in, it also considers the custom actions in the sequence.

The user data files are then moved to a per-machine location. To do so, go to the Files and Folders page and create a new folder called UserData under the Application Folder, then drag the previously created vlc folder under the Application Data and drop it under the newly created UserData. At the end, it should look like this:

![ai vlc user data per machine](https://cdn.advancedinstaller.com/img/best-practices-for-user-data/ai-vlc-user-data-per-machine.png "ai vlc user data per machine")  

We can now be certain that the files that must be copied on each user profile are always present on a per-machine basis, and that the files will be available even if the MSI is deleted. The final step is to create a custom action that copies the files from the UserData folder to the %appdata% folder.

As usual, we can do this either with VBScript or PowerShell. The code for the VBScript:

Dim objFSO, objShell
Set objFSO = CreateObject("Scripting.FileSystemObject")
Set objShell = CreateObject("WScript.Shell")
Dim sourceFolder, destinationFolder, programFilesPath, appDataPath
programFilesPath = objShell.SpecialFolders("ProgramW6432")
appDataPath = objShell.SpecialFolders("APPDATA")
sourceFolder = programFilesPath & "\VideoLAN\VLC\UserData"
destinationFolder = appDataPath & "\VLC"
    ' Copy the folder and its contents
    objFSO.CopyFolder sourceFolder, destinationFolder, True
Set objFSO = Nothing

Copy

The following actions are carried out by the code snippet:

* Creates objects for the FileSystemObject and WScript.Shell to access file system operations and special folder locations.
* Retrieves the paths for the Program Files folder (ProgramW6432) and the AppData folder (APPDATA) using the SpecialFolders property of the WScript.Shell object.
* Constructs the source folder path by appending the desired subfolder path (in this case, "\\VideoLAN\\VLC\\UserData") to the Program Files path.
* Constructs the destination folder path by appending the desired subfolder path (in this case, "\\VLC") to the AppData path.
* Uses the CopyFolder method of the FileSystemObject to copy the entire contents of the source folder to the destination folder. The third parameter (True) indicates that the operation should overwrite existing files if necessary.
* Releases the resources by setting the FileSystemObject to Nothing.

Then, launch Advanced Installer and go to the Custom Actions Page. Look for the Launch attached file and select the VBScript's location. Then, as shown below, configure the custom action to execute:

![ai vlc user data per machine vbscript](https://cdn.advancedinstaller.com/img/best-practices-for-user-data/ai-vlc-user-data-per-machine-vbscript.png "ai vlc user data per machine vbscript")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2105882/7443" target="_top" id="2105882">
  <img src="//a.impactradius-go.com/display-ad/7443-2105882" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2105882/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

The code for the PowerShell script:

$programfiles = $env:ProgramW6432
$appdata = $env:APPDATA
$sourcePath = $programfiles + "\VideoLAN\VLC\UserData"
$destinationPath = $appdata + "\VLC"

<!-- affiliate ads begin -->
<a href="https://bluettiit.sjv.io/c/5597632/2148129/17093" target="_top" id="2148129">
  <img src="//a.impactradius-go.com/display-ad/17093-2148129" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://bluettiit.sjv.io/i/5597632/2148129/17093" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

## Copy the folder and its contents recursively
Copy-Item -Path $sourcePath -Destination $destinationPath -Recurse -Force

Copy

The following actions are carried out by the code snippet:

* Retrieves the values of the Program Files directory and the AppData directory using environment variables ($env:ProgramW6432 and $env:APPDATA).
* Constructs the source folder path by appending the desired subfolder path ("\\VideoLAN\\VLC\\UserData") to the Program Files directory.
* Constructs the destination folder path by appending the desired subfolder path ("\\VLC") to the AppData directory.
* Uses the Copy-Item cmdlet in PowerShell to recursively copy the contents of the source folder to the destination folder. The -Recurse parameter ensures that all files and subdirectories are copied, and the -Force parameter overrides any restrictions that would prevent the copying operation.
* The files and directories from the source path are copied to the destination path.

Then, launch Advanced Installer and go to the Custom Actions Page. Search for the Run PowerShell script file and select the PowerShell script's location. Then, as shown below, configure the custom action to execute:

![ai vlc user data per machine powershell](https://cdn.advancedinstaller.com/img/best-practices-for-user-data/ai-vlc-user-data-per-machine-powershell.png "ai vlc user data per machine powershell")  

<!-- affiliate ads begin -->
<a href="https://versadesk.pxf.io/c/5597632/1815678/21290" target="_top" id="1815678">
  <img src="//a.impactradius-go.com/display-ad/21290-1815678" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://versadesk.pxf.io/i/5597632/1815678/21290" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Scenario two - Active Setup

The only difference between scenarios 1 and 2 is that in the active setup case, we disable the advertised shortcuts and do not require any other HKCU registry keys. After you've disabled the advertised shortcuts, go to the Product Details page and look for the Active Setup tab.

![ai vlc user data per machine active setup page](https://cdn.advancedinstaller.com/img/best-practices-for-user-data/ai-vlc-user-data-per-machine-active-setup-page.png "ai vlc user data per machine active setup page")  

<!-- affiliate ads begin -->
<a href="https://sentrypc.7eer.net/c/5597632/398455/3022" target="_top" id="398455">
  <img src="//a.impactradius-go.com/display-ad/3022-398455" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://sentrypc.7eer.net/i/5597632/398455/3022" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

In here, click on New and you can leave everything as default in the new window that appears.

![ai vlc user data per machine active setup config](https://cdn.advancedinstaller.com/img/best-practices-for-user-data/ai-vlc-user-data-per-machine-active-setup-config.png "ai vlc user data per machine active setup config")  

We have discussed more in-depth about the [Active Setup mechanism in our first book](https://tools.techidaily.com/advancedinstaller/products/), but if we check what the above settings mean we end up with the following:

* ID: The ID which will appear in the Active Setup registry. This can be basically anything because the Active Setup mechanism will check if on the current logged in user the registry for Active Setup which is present under HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Active Setup is also present under HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Active Setup
* Display Name: The purpose of the "DisplayName" value is to provide a meaningful name or description for the Active Setup component so that users can understand its purpose or functionality. It helps users identify the component when they view it in registry editors or other software that displays registry information.
* Stub Path: By setting the "StubPath" value, software developers can define the action or task that should be executed when the Active Setup component runs. It allows them to perform various installation or configuration operations during user logon, ensuring that specific tasks are completed for each user. In our case we are triggering a repair of the installed MSI with /fou.
* Locale: The purpose of the "Locale" value is to define the language or regional settings that should be used when executing the Active Setup component. It allows software developers to provide localized versions of their installation or configuration tasks, ensuring that the appropriate language or regional settings are applied for each user.
* Is Installed: Software developers can use the "IsInstalled" registry key to check the installation status of their Active Setup component. During the Active Setup process, the component can set or update the "IsInstalled" value based on the successful completion of its installation or configuration tasks. This allows subsequent logons by the user to skip the installation process if the component is already installed.

So the active setup is doing exactly what we need, and that is to trigger a repair of the MSI when the user logs in again.

And that is it, in both cases after the application is installed we have ensured that even after the deletion of the MSI the users will still be able to receive the user data files in their profile. The difference between the two scenarios are the following:

* If we are using the advertised shortcuts route, every time a HKCU registry is missing the self-healing will start again. Also, the self-healing will start immediately after the user starts any shortcuts, meaning that after the application gets installed the user will also have the configuration once he starts the application
* If we are using the active setup route, this will only be executed once. Another downside of this method is that the user must log off/log on again in order for the Active Setup mechanism to start running and find the differences

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
<li><a href="https://video-capture.techidaily.com/new-10-superior-tools-for-fbx-file-recording/"><u>[New] 10 Superior Tools for FBX File Recording</u></a></li>
<li><a href="https://fox-info.techidaily.com/updated-mastering-aquatic-cinematography-with-these-7-essential-strategies-for-2024/"><u>[Updated] Mastering Aquatic Cinematography with These 7 Essential Strategies for 2024</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/1-seamless-transfer-of-iphone-contacts-to-your-new-samsung-galaxy-s6/"><u>1. Seamless Transfer of iPhone Contacts to Your New Samsung Galaxy S6</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/comprehensive-analysis-of-wechats-in-built-video-chatting-feature-a-detailed-review/"><u>Comprehensive Analysis of WeChat's In-Built Video Chatting Feature: A Detailed Review</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/convert-mov-files-to-mp4-free-of-charge-a-simple-guide/"><u>Convert MOV Files to MP4 Free of Charge: A Simple Guide</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/easy-steps-to-create-an-alarm-reminder-on-your-android-device/"><u>Easy Steps to Create an Alarm Reminder on Your Android Device</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/experience-revolutionary-capabilities-the-new-apowermirror-arrives/"><u>Experience Revolutionary Capabilities: The New ApowerMirror Arrives</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/exposing-googles-5th-billion-scheme-understanding-the-scam-and-effective-elimination-techniques/"><u>Exposing Google's 5Th Billion Scheme: Understanding the Scam & Effective Elimination Techniques</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/guide-to-broadcasting-your-gameplay-mastering-lcs-style-livestreams-with-wild-rift/"><u>Guide to Broadcasting Your Gameplay: Mastering LCS-Style Livestreams with Wild Rift</u></a></li>
<li><a href="https://location-social.techidaily.com/how-to-detect-and-stop-mspy-from-spying-on-your-honor-magic-6-lite-drfone-by-drfone-virtual-android/"><u>How to Detect and Stop mSpy from Spying on Your Honor Magic 6 Lite | Dr.fone</u></a></li>
<li><a href="https://win-solutions.techidaily.com/how-to-resolve-constant-freezing-issues-in-wwe-2k22-for-pc-players/"><u>How To Resolve Constant Freezing Issues in WWE 2K22 for PC Players</u></a></li>
<li><a href="https://location-social.techidaily.com/in-2024-how-to-change-location-on-tiktok-to-see-more-content-on-your-tecno-pova-6-pro-5g-drfone-by-drfone-virtual-android/"><u>In 2024, How to Change Location on TikTok to See More Content On your Tecno Pova 6 Pro 5G | Dr.fone</u></a></li>
<li><a href="https://easy-unlock-android.techidaily.com/in-2024-still-using-pattern-locks-with-oneplus-ace-2v-tips-tricks-and-helpful-advice-by-drfone-android/"><u>In 2024, Still Using Pattern Locks with OnePlus Ace 2V? Tips, Tricks and Helpful Advice</u></a></li>
<li><a href="https://buynow-info.techidaily.com/in-depth-analysis-unpacking-the-powerful-samsung-gear-s3-frontier-with-multifaceted-capabilities/"><u>In-Depth Analysis: Unpacking the Powerful Samsung Gear S3 Frontier with Multifaceted Capabilities</u></a></li>
<li><a href="https://techtrends.techidaily.com/reviving-your-amazon-prime-captions-solutions-for-non-functioning-subtitles/"><u>Reviving Your Amazon Prime Captions: Solutions for Non-Functioning Subtitles</u></a></li>
<li><a href="https://tech-savvy.techidaily.com/step-by-step-guide-adding-subtitles-when-creating-a-dvd/"><u>Step-by-Step Guide: Adding Subtitles when Creating a DVD</u></a></li>
<li><a href="https://driver-download.techidaily.com/step-by-step-tutorial-on-downloading-intels-nvme-drivers-for-optimal-performance/"><u>Step-by-Step Tutorial on Downloading Intel's NVMe Drivers for Optimal Performance</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/ultimate-guide-creating-your-ideal-clubhouse-image-with-ease/"><u>Ultimate Guide: Creating Your Ideal Clubhouse Image with Ease</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/understanding-email-impersonation-techniques-and-defense-strategies/"><u>Understanding Email Impersonation: Techniques & Defense Strategies</u></a></li>
</ul></div>

