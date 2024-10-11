---
title: "How to Edit the Hosts File Using VBScript or PowerShell: A Step-by-Step Guide"
date: 2024-10-07T03:11:14.639Z
updated: 2024-10-10T20:03:39.749Z
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
<a href="https://aligracehair.sjv.io/c/5597632/2047361/19272" target="_top" id="2047361">
  <img src="//a.impactradius-go.com/display-ad/19272-2047361" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2047361/19272" style="position:absolute;visibility:hidden;" border="0" />
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

### Write in hosts file with PowerShell

If you want to use PowerShell to write in the hosts file, this is also quite easy to accomplish.

$hostsFilePath = "$env:SystemRoot\System32\drivers\etc\hosts"

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2135402/19272" target="_top" id="2135402">
  <img src="//a.impactradius-go.com/display-ad/19272-2135402" border="0" alt="https://techidaily.com" width="336" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2135402/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

## Specify the hostname and IP address
$hostname = "example.com"
$ipAddress = "127.0.0.1"

<!-- affiliate ads begin -->
<span id="1424529">
					<video width="864" height="1536" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1424529.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/16446-1424529">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1424529.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:540px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Flaganoo.pxf.io%2Fc%2F5597632%2F1424529%2F16446'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1424529/16446" style="position:absolute;visibility:hidden;" border="0" />
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
<a href="https://appsumo.8odi.net/c/5597632/2037351/7443" target="_top" id="2037351">
  <img src="//a.impactradius-go.com/display-ad/7443-2037351" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2037351/7443" style="position:absolute;visibility:hidden;" border="0" />
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
<li><a href="https://facebook-video-content.techidaily.com/new-a-comprehensive-list-of-excellent-fb-cover-photo-creators-for-2024/"><u>[New] A Comprehensive List of Excellent FB Cover Photo Creators for 2024</u></a></li>
<li><a href="https://some-knowledge.techidaily.com/updated-full-review-of-the-latest-facetune-features-and-fixes/"><u>[Updated] Full Review of the Latest Facetune Features and Fixes</u></a></li>
<li><a href="https://youtube-lab.techidaily.com/approved-crafting-perfect-thumbnails-for-higher-clickthrough-rates/"><u>2024 Approved Crafting Perfect Thumbnails for Higher Clickthrough Rates</u></a></li>
<li><a href="https://extra-guidance.techidaily.com/2024-approved-pushing-creative-boundaries-utilizing-advanced-techniques-for-luts-in-after-effects/"><u>2024 Approved Pushing Creative Boundaries Utilizing Advanced Techniques for LUTs in After Effects</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/comprehensive-guide-to-over-12-malware-varieties-definitions-and-real-world-instances/"><u>Comprehensive Guide to Over 12 Malware Varieties: Definitions & Real-World Instances</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/explore-best-substitutes-of-xsplit-for-both-pcs-and-apple-computers/"><u>Explore Best Substitutes of Xsplit for Both PCs and Apple Computers</u></a></li>
<li><a href="https://some-knowledge.techidaily.com/exploring-types-and-methods-of-touchless-technology-for-2024/"><u>Exploring Types and Methods of Touchless Technology for 2024</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/implementing-windows-management-scripts-through-intunes-msix-technology/"><u>Implementing Windows Management Scripts Through Intune's MSIX Technology</u></a></li>
<li><a href="https://sim-unlock.techidaily.com/in-2024-three-ways-to-sim-unlock-realme-11-5g-by-drfone-android/"><u>In 2024, Three Ways to Sim Unlock Realme 11 5G</u></a></li>
<li><a href="https://facebook-videos.techidaily.com/in-2024-transform-your-chronicles-free-extensions-and-mobile-apps-galore/"><u>In 2024, Transform Your Chronicles FREE Extensions & Mobile Apps Galore</u></a></li>
<li><a href="https://screen-recording.techidaily.com/in-2024-unlock-superior-mac-gif-capture-with-these-apps/"><u>In 2024, Unlock Superior Mac GIF Capture with These Apps</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/mastering-zepto-usage-a-comprehensive-guide-for-desktop-enthusiasts/"><u>Mastering Zepto Usage: A Comprehensive Guide for Desktop Enthusiasts</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/the-mechanics-behind-malicious-software-distribution-via-spam-emails-explained/"><u>The Mechanics Behind Malicious Software Distribution via Spam Emails Explained</u></a></li>
</ul></div>

