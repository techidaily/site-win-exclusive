---
title: "How to Edit the Hosts File Using VBScript or PowerShell: A Step-by-Step Guide"
date: 2024-09-27T07:22:16.627Z
updated: 2024-09-29T19:12:10.052Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: "This Article Describes How to Edit the Hosts File Using VBScript or PowerShell: A Step-by-Step Guide"
thumbnail: https://thmb.techidaily.com/0138e2483878b61786c62e2e9ead335ddaa2649c1800ba21659cf76cde33dc5d.jpg
---

## How to Edit the Hosts File Using VBScript or PowerShell: A Step-by-Step Guide

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
<a href="https://ephamedtechinc.pxf.io/c/5597632/2136614/26400" target="_top" id="2136614">
  <img src="//a.impactradius-go.com/display-ad/26400-2136614" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://ephamedtechinc.pxf.io/i/5597632/2136614/26400" style="position:absolute;visibility:hidden;" border="0" />
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
<a href="https://25home.pxf.io/c/5597632/2148648/16836" target="_top" id="2148648">
  <img src="//a.impactradius-go.com/display-ad/16836-2148648" border="0" alt="https://techidaily.com" width="468" height="60"/>
</a>
<img height="0" width="0" src="https://25home.pxf.io/i/5597632/2148648/16836" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Write in hosts file with PowerShell

If you want to use PowerShell to write in the hosts file, this is also quite easy to accomplish.

$hostsFilePath = "$env:SystemRoot\System32\drivers\etc\hosts"
## Specify the hostname and IP address
$hostname = "example.com"
$ipAddress = "127.0.0.1"

<!-- affiliate ads begin -->
<span id="1444782">
					<video width="1024" height="576" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1444782.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/14559-1444782">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1444782.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:640px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fpropmoneyinc.pxf.io%2Fc%2F5597632%2F1444782%2F14559'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1444782/14559" style="position:absolute;visibility:hidden;" border="0" />
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
<a href="https://appsumo.8odi.net/c/5597632/2144274/7443" target="_top" id="2144274">
  <img src="//a.impactradius-go.com/display-ad/7443-2144274" border="0" alt="https://techidaily.com" width="600" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2144274/7443" style="position:absolute;visibility:hidden;" border="0" />
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
<li><a href="https://article-posts.techidaily.com/new-the-ultimate-guide-to-choosing-between-gopro-and-yi-for-2024/"><u>[New] The Ultimate Guide to Choosing Between GoPro and Yi for 2024</u></a></li>
<li><a href="https://some-knowledge.techidaily.com/2024-approved-hps-color-expertise-in-full-display-the-z32x-review/"><u>2024 Approved HP's Color Expertise in Full Display The Z32X Review</u></a></li>
<li><a href="https://instagram-videos.techidaily.com/2024-approved-mute-instagrams-personalized-posts/"><u>2024 Approved Mute Instagram's Personalized Posts</u></a></li>
<li><a href="https://discover-exclusive.techidaily.com/1725288408997-dvdusb/"><u>DVDからUSBメモリーへのコピー - 安全で自由にダウンロード</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/1726027810416-flacmp3/"><u>FLAC形式へのMP3ファイル変換手順 - ステップバイステップガイド</u></a></li>
<li><a href="https://android-location-track.techidaily.com/how-to-track-oneplus-ace-2-location-by-number-drfone-by-drfone-virtual-android/"><u>How to Track OnePlus Ace 2 Location by Number | Dr.fone</u></a></li>
<li><a href="https://review-topics.techidaily.com/in-2024-complete-tutorial-to-use-gps-joystick-to-fake-gps-location-on-infinix-hot-30i-drfone-by-drfone-virtual-android/"><u>In 2024, Complete Tutorial to Use GPS Joystick to Fake GPS Location On Infinix Hot 30i | Dr.fone</u></a></li>
<li><a href="https://bypass-frp.techidaily.com/in-2024-full-guide-to-bypass-honor-frp-by-drfone-android/"><u>In 2024, Full Guide to Bypass Honor FRP</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/1726030474539-ituneswav/"><u>ITunesから直接WAVファイル:カンタンに変換方法解説</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/1726029811365-mpeg-4/"><u>MPEG-4変換手順ガイド - 動画に最適化</u></a></li>
<li><a href="https://windows11.techidaily.com/win-11-proxies-a-practical-guide-to-enhanced-privacy/"><u>Win 11 Proxies: A Practical Guide to Enhanced Privacy</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/win-the-new-wonderfox-collection-free-prize-and-special-deals-for-back-to-school-season-2014/"><u>Win the New WonderFox Collection – Free Prize & Special Deals for Back to School Season, 2014!</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/youtubemp3/"><u>YouTubeからMP3プレーヤーに楽曲転送テクニック</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/44ot44oh44kq44o744of44ol44o844k444od44kv44ov44kh44kk44or55so6zplusz5aow44kz44o844oh44od44kv5asj5pu05oml6acg44ks44kk44oj/"><u>ビデオ・ミュージックファイル用音声コーデック変更手順ガイド</u></a></li>
</ul></div>

