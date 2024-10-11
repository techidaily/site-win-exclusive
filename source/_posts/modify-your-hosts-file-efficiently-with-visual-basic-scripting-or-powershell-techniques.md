---
title: Modify Your Hosts File Efficiently with Visual Basic Scripting or PowerShell Techniques
date: 2024-10-06T00:33:21.358Z
updated: 2024-10-10T16:18:06.379Z
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
<a href="https://ephamedtechinc.pxf.io/c/5597632/2126493/26400" target="_top" id="2126493">
  <img src="//a.impactradius-go.com/display-ad/26400-2126493" border="0" alt="https://techidaily.com" width="640" height="90"/>
</a>
<img height="0" width="0" src="https://ephamedtechinc.pxf.io/i/5597632/2126493/26400" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Write in hosts file with PowerShell

If you want to use PowerShell to write in the hosts file, this is also quite easy to accomplish.

$hostsFilePath = "$env:SystemRoot\System32\drivers\etc\hosts"

<!-- affiliate ads begin -->
<a href="https://versadesk.pxf.io/c/5597632/1828647/21290" target="_top" id="1828647">
  <img src="//a.impactradius-go.com/display-ad/21290-1828647" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://versadesk.pxf.io/i/5597632/1828647/21290" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

## Specify the hostname and IP address
$hostname = "example.com"
$ipAddress = "127.0.0.1"

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2144272/7443" target="_top" id="2144272">
  <img src="//a.impactradius-go.com/display-ad/7443-2144272" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2144272/7443" style="position:absolute;visibility:hidden;" border="0" />
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
<a href="https://appsumo.8odi.net/c/5597632/2144281/7443" target="_top" id="2144281">
  <img src="//a.impactradius-go.com/display-ad/7443-2144281" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2144281/7443" style="position:absolute;visibility:hidden;" border="0" />
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
<li><a href="https://on-screen-recording.techidaily.com/updated-capturing-playthroughs-on-windows-10-easy-way/"><u>[Updated] Capturing Playthroughs on Windows 10 Easy Way</u></a></li>
<li><a href="https://screen-recording.techidaily.com/updated-capturing-tv-screen-scenes-with-ease-your-ultimate-guide/"><u>[Updated] Capturing TV Screen Scenes with Ease - Your Ultimate Guide</u></a></li>
<li><a href="https://extra-information.techidaily.com/2024-approved-avoid-hassle-effortless-addition-of-video-content-in-youtube-plays/"><u>2024 Approved Avoid Hassle Effortless Addition of Video Content in YouTube Plays</u></a></li>
<li><a href="https://video-capture.techidaily.com/2024-approved-perfecting-live-steam-playback-a-step-by-step-approach/"><u>2024 Approved Perfecting Live Steam Playback A Step-by-Step Approach</u></a></li>
<li><a href="https://youtube-zero.techidaily.com/approved-streamline-your-youtube-experience-shareable-playlists/"><u>2024 Approved Streamline Your YouTube Experience Shareable Playlists</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/comprehensive-android-security-manual-eradicating-and-fortifying-your-mobile-device-against-malware/"><u>Comprehensive Android Security Manual: Eradicating & Fortifying Your Mobile Device Against Malware</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/comprehensive-tutorials-creating-interactive-pdf-forms-step-by-step/"><u>Comprehensive Tutorials: Creating Interactive PDF Forms Step-by-Step</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/effortless-ways-to-cast-your-huawei-p50-on-the-big-screen/"><u>Effortless Ways to Cast Your Huawei P50 on the Big Screen</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/innovative-methods-for-reflecting-your-ipad-display-onto-a-pc/"><u>Innovative Methods for Reflecting Your iPad Display Onto a PC</u></a></li>
<li><a href="https://fox-access.techidaily.com/mastering-iphone-photo-blurring-4-techniques-explored/"><u>Mastering iPhone Photo Blurring 4 Techniques Explored</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/mastering-safe-communication-a-step-by-step-guide-on-protected-email-dispatch-in-gmail-and-outlook/"><u>Mastering Safe Communication: A Step-by-Step Guide on Protected Email Dispatch in Gmail and Outlook</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/understanding-rat-malware-prevention-strategies-against-remote-access-trojans/"><u>Understanding RAT Malware: Prevention Strategies Against Remote Access Trojans</u></a></li>
<li><a href="https://extra-lessons.techidaily.com/unleash-hdr-potential-the-comprehensive-sdr-to-hdr-conversion-guide/"><u>Unleash HDR Potential The Comprehensive SDR-to-HDR Conversion Guide</u></a></li>
<li><a href="https://ai-driven-video-production.techidaily.com/updated-unleash-your-creativity-top-video-animation-apps-for-smartphone-and-tablet-users/"><u>Updated Unleash Your Creativity Top Video Animation Apps for Smartphone and Tablet Users</u></a></li>
</ul></div>

