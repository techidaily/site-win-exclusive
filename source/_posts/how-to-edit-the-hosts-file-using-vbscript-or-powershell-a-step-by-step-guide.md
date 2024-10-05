---
title: "How to Edit the Hosts File Using VBScript or PowerShell: A Step-by-Step Guide"
date: 2024-09-29T20:04:06.630Z
updated: 2024-10-05T19:59:57.710Z
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
<a href="https://aligracehair.sjv.io/c/5597632/1948909/19272" target="_top" id="1948909">
  <img src="//a.impactradius-go.com/display-ad/19272-1948909" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1948909/19272" style="position:absolute;visibility:hidden;" border="0" />
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
<a href="https://wigfever.sjv.io/c/5597632/2014849/22899" target="_top" id="2014849">
  <img src="//a.impactradius-go.com/display-ad/22899-2014849" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://wigfever.sjv.io/i/5597632/2014849/22899" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Write in hosts file with PowerShell

If you want to use PowerShell to write in the hosts file, this is also quite easy to accomplish.

$hostsFilePath = "$env:SystemRoot\System32\drivers\etc\hosts"
## Specify the hostname and IP address
$hostname = "example.com"
$ipAddress = "127.0.0.1"

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2043596/7443" target="_top" id="2043596">
  <img src="//a.impactradius-go.com/display-ad/7443-2043596" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2043596/7443" style="position:absolute;visibility:hidden;" border="0" />
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
<a href="https://aligracehair.sjv.io/c/5597632/2087253/19272" target="_top" id="2087253">
  <img src="//a.impactradius-go.com/display-ad/19272-2087253" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2087253/19272" style="position:absolute;visibility:hidden;" border="0" />
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
<li><a href="https://facebook-clips.techidaily.com/new-2024-approved-aspect-ratio-for-video-content-on-social-platforms/"><u>[New] 2024 Approved Aspect Ratio for Video Content on Social Platforms</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/comparative-techniques-in-software-remastering-insights-into-msi-and-exe-conversion-strategies/"><u>Comparative Techniques in Software Remastering: Insights Into MSI and EXE Conversion Strategies</u></a></li>
<li><a href="https://screen-recording.techidaily.com/datasafe-experts-assessment-for-2024/"><u>DataSafe Experts Assessment for 2024</u></a></li>
<li><a href="https://tech-recovery.techidaily.com/decoding-the-503-error-code-causes-impacts-and-remedies/"><u>Decoding the 503 Error Code: Causes, Impacts, and Remedies</u></a></li>
<li><a href="https://technical-tips.techidaily.com/gmail-hack-proof-effective-ways-to-manage-and-add-multiple-emails-securely/"><u>Gmail Hack-Proof: Effective Ways to Manage and Add Multiple Emails Securely</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/id3-tagger-quickly-assign-metadata-to-your-audio-library-for-enhanced-discoverability/"><u>ID3 Tagger: Quickly Assign Metadata to Your Audio Library for Enhanced Discoverability</u></a></li>
<li><a href="https://fake-location.techidaily.com/in-2024-3-ways-to-change-location-on-facebook-marketplace-for-zte-axon-40-lite-drfone-by-drfone-virtual-android/"><u>In 2024, 3 Ways to Change Location on Facebook Marketplace for ZTE Axon 40 Lite | Dr.fone</u></a></li>
<li><a href="https://discover-extraordinary.techidaily.com/kostenlose-dvd-decodierungssoftware-fur-windows-10-and-macos-herunterladen/"><u>Kostenlose DVD-Decodierungssoftware Für Windows 10 & macOS - Herunterladen</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/master-the-art-of-a-clean-browsing-experience-with-these-4-techniques-to-block-and-remove-pop-ups-from-firefox/"><u>Master the Art of a Clean Browsing Experience with These 4 Techniques to Block & Remove Pop-Ups From Firefox</u></a></li>
<li><a href="https://win11.techidaily.com/navigating-asana-setbacks-a-guide-for-windows-users/"><u>Navigating Asana Setbacks: A Guide for Windows Users</u></a></li>
<li><a href="https://video-capture.techidaily.com/the-gamers-blueprint-techniques-to-record-virtual-realms-for-2024/"><u>The Gamer's Blueprint Techniques to Record Virtual Realms for 2024</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/top-5-multifaceted-antivirus-scanners-expert-reviews-and-comparisons/"><u>Top 5 Multifaceted Antivirus Scanners: Expert Reviews and Comparisons</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/unraveling-the-mystery-why-does-my-chrome-display-managed-by-an-organization-and-is-it-safe/"><u>Unraveling the Mystery: Why Does My Chrome Display 'Managed By an Organization,' And Is It Safe?</u></a></li>
<li><a href="https://video-creation-software.techidaily.com/updated-2024-approved-get-started-with-mp4-video-editing-a-friendly-tutorial-for-mac-and-windows-beginners/"><u>Updated 2024 Approved Get Started with MP4 Video Editing A Friendly Tutorial for Mac and Windows Beginners</u></a></li>
</ul></div>

