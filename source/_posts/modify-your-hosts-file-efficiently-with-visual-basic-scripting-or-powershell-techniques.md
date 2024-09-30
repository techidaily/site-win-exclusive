---
title: Modify Your Hosts File Efficiently with Visual Basic Scripting or PowerShell Techniques
date: 2024-09-23T03:57:59.567Z
updated: 2024-09-29T22:06:33.078Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: This Article Describes Modify Your Hosts File Efficiently with Visual Basic Scripting or PowerShell Techniques
thumbnail: https://thmb.techidaily.com/db7a51fc88bb312b4c001dc26d2d013159de6bfbef053f36ef148640b15c567b.jpg
---

## Modify Your Hosts File Efficiently with Visual Basic Scripting or PowerShell Techniques

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Write line in hosts file

On the Windows operating system, the hosts file is a plain text file that maps hostnames to IP addresses. It functions as a local DNS (Domain Name System) resolver, allowing you to specify the IP address associated with a specific hostname.

The hosts file is located at %SystemRoot%\\System32\\drivers\\etc\\hosts, where %SystemRoot% represents the Windows installation directory (e.g., C:\\Windows). The file has no file extension by default and is just titled "hosts."

Each line in the hosts file begins with an IP address and ends with one or more hostnames, separated by spaces or tabs. As an example:

127.0.0.1       localhost

Copy

The IP address 127.0.0.1 is associated with the hostname localhost in this example. In a web browser, typing localhost will resolve to the specified IP address.

To add custom mappings between hostnames and IP addresses, manually edit the hosts file. This can be useful for a variety of purposes, including redirecting a domain name to a different IP address for testing or blocking access to specific websites by redirecting them to a non-existent or local IP address.

Please keep in mind that editing the hosts file usually necessitates administrative privileges. As a result, you may need to use an administrator account to run a text editor or any program that modifies the hosts file.

There might be cases where the modification of the hosts file is required directly from the MSI package, and the only way to do this is only via Custom Actions.

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2111994/7443" target="_top" id="2111994">
  <img src="//a.impactradius-go.com/display-ad/7443-2111994" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2111994/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Write in hosts file with VBScript

If you want to use VBScript to write in the hosts file, this is quite easy to accomplish.

Const ForReading = 1
Const ForWriting = 2
Const HostsFilePath = "C:\Windows\System32\drivers\etc\hosts"
Dim objFSO, objFile
Dim strIPAddress, strHostname, strNewEntry
' Prompt user for the IP address and hostname
strIPAddress = “127.0.0.1”
strHostname = “example.com”
' Create the new hosts file entry
strNewEntry = strIPAddress & vbTab & strHostname
' Open the hosts file for appending
Set objFSO = CreateObject("Scripting.FileSystemObject")
Set objFile = objFSO.OpenTextFile(HostsFilePath, ForAppending, True)
' Check if the entry already exists in the hosts file
Do Until objFile.AtEndOfStream
    If LCase(objFile.ReadLine) = LCase(strNewEntry) Then
        MsgBox "The entry already exists in the hosts file."
        objFile.Close
        WScript.Quit
    End If
Loop
' Close the file and reopen it for writing
objFile.Close
Set objFile = objFSO.OpenTextFile(HostsFilePath, ForAppending, True)
' Write the new entry to the hosts file
objFile.WriteLine(strNewEntry)
objFile.Close

Copy

The above VBScript performs the following actions:

* It defines constants for file reading (ForReading) and file writing (ForWriting) modes, and specifies the path to the hosts file (HostsFilePath), which is typically located at "C:\\Windows\\System32\\drivers\\etc\\hosts".
* It declares variables to store the IP address, hostname, and the new entry that will be added to the hosts file.
* The IP address is set to "127.0.0.1" (loopback address) and the hostname is set to "example.com".
* It creates a string (strNewEntry) by combining the IP address and hostname, separated by a tab character.
* It uses the FileSystemObject to access the hosts file and open it in appending mode (ForAppending). If the hosts file doesn't exist, it will be created.
* It reads each line of the hosts file to check if the new entry already exists. If a matching entry is found, a message box is displayed, and the script terminates.
* If the entry is not found, the file is closed and reopened in appending mode to write the new entry using the WriteLine method.
* Once the new entry is written, the file is closed again.

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1975836/19272" target="_top" id="1975836">
  <img src="//a.impactradius-go.com/display-ad/19272-1975836" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1975836/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Write in hosts file with PowerShell

If you want to use PowerShell to write in the hosts file, this is also quite easy to accomplish.

$hostsFilePath = "$env:SystemRoot\System32\drivers\etc\hosts"
## Specify the hostname and IP address
$hostname = "example.com"
$ipAddress = "127.0.0.1"

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2135398/19272" target="_top" id="2135398">
  <img src="//a.impactradius-go.com/display-ad/19272-2135398" border="0" alt="https://techidaily.com" width="250" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2135398/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

## Check if the hosts file exists
if (Test-Path $hostsFilePath) {
# Check if the entry already exists in the hosts file
    $existingEntry = Get-Content $hostsFilePath | Where-Object { $_ -like "$ipAddress *$hostname*" }
    if ($existingEntry) {
        Write-Host "Entry already exists in the hosts file."

    else {
# Append the new entry to the hosts file
        $newEntry = "$ipAddress $hostname"
        Add-Content -Path $hostsFilePath -Value $newEntry
        Write-Host "Entry added to the hosts file."

else {
    Write-Host "Hosts file not found."

Copy

The script performs the following actions:

* $hostsFilePath: Specifies the path to the hosts file (C:\\Windows\\System32\\drivers\\etc\\hosts).
* $hostname: Specifies the hostname to be added to the hosts file.
* $ipAddress: Specifies the corresponding IP address for the hostname.
* if (Test-Path $hostsFilePath) { ... }: Checks if the hosts file exists at the specified path. If it does, the script proceeds to modify the file. Otherwise, it outputs a message indicating that the hosts file was not found.
* $existingEntry = Get-Content $hostsFilePath | Where-Object { $\_ -like "$ipAddress \*$hostname\*" }: Reads the content of the hosts file and searches for an existing entry that matches the specified IP address and hostname. If a matching entry is found, it is stored in the $existingEntry variable.
* if ($existingEntry) { ... }: Checks if an existing entry was found in the hosts file. If so, it outputs a message indicating that the entry already exists.
* else { ... }: If no existing entry was found, the script continues to add the new entry to the hosts file.
* $newEntry = "$ipAddress $hostname": Constructs the new entry by combining the IP address and hostname.
* Add-Content -Path $hostsFilePath -Value $newEntry: Appends the new entry to the hosts file using the Add-Content cmdlet.
* Write-Host "Entry added to the hosts file.": Outputs a message indicating that the new entry has been successfully added to the hosts file.

The script checks if the hosts file exists and if the entry already exists in the file. If the entry is found, it displays a message indicating that the entry already exists. If the entry doesn't exist, it appends the new entry to the hosts file using the Add-Content cmdlet.

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)I have compiled a list of the most used scripts in Software Packaging that you can download from [here](https://www.alexandrumarin.com/downloads/#packaging-script-collection "here").  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2094482/7443" target="_top" id="2094482">
  <img src="//a.impactradius-go.com/display-ad/7443-2094482" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2094482/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

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
<li><a href="https://fox-glue.techidaily.com/new-in-2024-unlocking-new-dimensions-in-physical-interaction-tech/"><u>[New] In 2024, Unlocking New Dimensions in Physical Interaction Tech</u></a></li>
<li><a href="https://instagram-video-recordings.techidaily.com/updated-engaging-followers-on-instagram-with-youtube-video-links-in-stories/"><u>[Updated] Engaging Followers on Instagram with YouTube Video Links in Stories</u></a></li>
<li><a href="https://facebook-video-footage.techidaily.com/updated-in-2024-cutting-edge-editors-elevating-online-videos/"><u>[Updated] In 2024, Cutting-Edge Editors Elevating Online Videos</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/filemaker/"><u>「音楽・動画をFileMakerで正常にインポートするための対策ガイド」</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/1726027560661-mkv/"><u>最適な非劣化編集ツール：MKVファイルの基本から上達までガイド</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/1726029516744-chrome/"><u>Chromeビデオ再生に問題が発生したときの解決手段</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/convert-your-favorite-vimeo-videos-into-mp4-format-with-these-5-simple-cost-free-methods/"><u>Convert Your Favorite Vimeo Videos Into MP4 Format with These 5 Simple, Cost-Free Methods</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/easy-steps-to-change-trp-videos-to-ts-format-without-a-hitch/"><u>Easy Steps to Change TRP Videos to TS Format without a Hitch</u></a></li>
<li><a href="https://win-answers.techidaily.com/essential-fixes-for-dragons-dogma-2-crashing-issues-on-windowsmac/"><u>Essential Fixes for Dragon's Dogma 2 Crashing Issues on Windows/Mac</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/expert-guide-ultimate-hd-video-processing-toolkit-with-feature-rich-factory-pro-applications/"><u>Expert Guide: Ultimate HD Video Processing Toolkit with Feature-Rich Factory Pro Applications</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/factory-or-pro-key-advantages-of-the-two-versions-of-nokia-video-converter/"><u>Factory or Pro? Key Advantages of the Two Versions of Nokia Video Converter</u></a></li>
<li><a href="https://hardware-tips.techidaily.com/harness-unmatched-thermal-efficiency-with-pioneercools-ultrafrost-duo-aio-liquid-cooler/"><u>Harness Unmatched Thermal Efficiency with PioneerCool's UltraFrost-Duo AIO Liquid Cooler</u></a></li>
<li><a href="https://location-social.techidaily.com/how-to-send-and-fake-live-location-on-facebook-messenger-of-your-oppo-a79-5g-drfone-by-drfone-virtual-android/"><u>How to Send and Fake Live Location on Facebook Messenger Of your Oppo A79 5G | Dr.fone</u></a></li>
<li><a href="https://driver-install.techidaily.com/navigating-vistas-hardware-management-without-gui/"><u>Navigating Vista's Hardware Management Without GUI</u></a></li>
<li><a href="https://android-unlock.techidaily.com/still-using-pattern-locks-with-samsung-galaxy-xcover-6-pro-tactical-edition-tips-tricks-and-helpful-advice-by-drfone-android/"><u>Still Using Pattern Locks with Samsung Galaxy XCover 6 Pro Tactical Edition? Tips, Tricks and Helpful Advice</u></a></li>
<li><a href="https://fake-location.techidaily.com/what-is-fake-gps-location-pro-and-is-it-good-on-vivo-g2-drfone-by-drfone-virtual-android/"><u>What is Fake GPS Location Pro and Is It Good On Vivo G2? | Dr.fone</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/1726029858827-youtubedvd/"><u>YouTube上でDVDデータを効率よくアップロードする方法説明 - ユーザーフレンドリーなチュートリアル</u></a></li>
</ul></div>

