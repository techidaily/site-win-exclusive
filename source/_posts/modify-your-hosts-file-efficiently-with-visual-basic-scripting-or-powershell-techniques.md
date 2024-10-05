---
title: Modify Your Hosts File Efficiently with Visual Basic Scripting or PowerShell Techniques
date: 2024-10-02T19:38:03.868Z
updated: 2024-10-05T18:53:06.386Z
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
<a href="https://appsumo.8odi.net/c/5597632/2100527/7443" target="_top" id="2100527">
  <img src="//a.impactradius-go.com/display-ad/7443-2100527" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2100527/7443" style="position:absolute;visibility:hidden;" border="0" />
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
<a href="https://appsumo.8odi.net/c/5597632/2130874/7443" target="_top" id="2130874">
  <img src="//a.impactradius-go.com/display-ad/7443-2130874" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2130874/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

## Specify the hostname and IP address
$hostname = "example.com"
$ipAddress = "127.0.0.1"

<!-- affiliate ads begin -->
<a href="https://bluettius.sjv.io/c/5597632/2139113/17108" target="_top" id="2139113">
  <img src="//a.impactradius-go.com/display-ad/17108-2139113" border="0" alt="https://techidaily.com" width="320" height="90"/>
</a>
<img height="0" width="0" src="https://bluettius.sjv.io/i/5597632/2139113/17108" style="position:absolute;visibility:hidden;" border="0" />
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
<a href="https://aligracehair.sjv.io/c/5597632/1885947/19272" target="_top" id="1885947">
  <img src="//a.impactradius-go.com/display-ad/19272-1885947" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1885947/19272" style="position:absolute;visibility:hidden;" border="0" />
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
<li><a href="https://screen-video-capture.techidaily.com/new-2024-approved-simplify-lenovo-screen-casting-today/"><u>[New] 2024 Approved Simplify Lenovo Screen Casting Today</u></a></li>
<li><a href="https://vp-tips.techidaily.com/new-adding-soundtracks-to-your-inshot-projects-for-2024/"><u>[New] Adding Soundtracks to Your InShot Projects for 2024</u></a></li>
<li><a href="https://extra-guidance.techidaily.com/new-best-8-online-photo-montage-maker/"><u>[New] Best 8 Online Photo Montage Maker</u></a></li>
<li><a href="https://facebook-video-content.techidaily.com/updated-2024-approved-smart-tv-meets-social-networks-televising-fb-content/"><u>[Updated] 2024 Approved Smart TV Meets Social Networks Televising FB Content</u></a></li>
<li><a href="https://tech-haven.techidaily.com/6-effective-strategies-leveraging-chatgpt-for-enhanced-job-hunting/"><u>6 Effective Strategies: Leveraging ChatGPT for Enhanced Job Hunting</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/a-comprehensive-guide-streaming-moba-fun-from-mobile-legends-to-your-pc/"><u>A Comprehensive Guide: Streaming MOBA Fun From Mobile Legends to Your PC</u></a></li>
<li><a href="https://smart-video-creator.techidaily.com/background-noise-begone-mastering-audio-editing-in-final-cut-pro-x/"><u>Background Noise Begone! Mastering Audio Editing in Final Cut Pro X</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/best-security-question-practices-a-comprehensive-guide-to-enhancing-your-online-safety/"><u>Best Security Question Practices: A Comprehensive Guide to Enhancing Your Online Safety</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/comprehensive-evaluation-of-screencast-o-matic-features-and-performance/"><u>Comprehensive Evaluation of Screencast-O-Matic: Features and Performance</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/comprehensive-msi-academy-online-tutorials/"><u>Comprehensive MSI Academy Online Tutorials</u></a></li>
<li><a href="https://techno-recovery.techidaily.com/discover-the-latest-budget-friendly-study-apps-for-students-preparing-for-school/"><u>Discover the Latest Budget-Friendly Study Apps for Students Preparing for School</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/easy-steps-moving-your-contacts-and-files-from-an-old-iphone-to-a-new-iphone-xs/"><u>Easy Steps: Moving Your Contacts and Files From an Old iPhone to a New iPhone XS</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/imovie-compatible-video-format-transformer-how-to-optimize-videos-for-seamless-editing/"><u>IMovie Compatible Video Format Transformer: How to Optimize Videos for Seamless Editing</u></a></li>
<li><a href="https://extra-information.techidaily.com/in-2024-clearsnap-guide-how-to-exclude-distracting-picture-borders/"><u>In 2024, ClearSnap Guide How to Exclude Distracting Picture Borders</u></a></li>
<li><a href="https://activate-lock.techidaily.com/in-2024-unlocking-an-icloud-locked-ipad-and-iphone-13-pro-by-drfone-ios/"><u>In 2024, Unlocking an iCloud Locked iPad and iPhone 13 Pro</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/mastering-the-art-of-opera-screen-captures-a-comprehensive-guide/"><u>Mastering the Art of Opera Screen Captures: A Comprehensive Guide</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/navigating-cyber-threats-understanding-the-dangers-of-suspicious-pdfs-on-mobile-devices-with-malwarefox-insights/"><u>Navigating Cyber Threats: Understanding the Dangers of Suspicious PDFs on Mobile Devices with MalwareFox Insights</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/top-free-software-for-converting-flv-videos-into-3gp-format/"><u>Top Free Software for Converting FLV Videos Into 3GP Format</u></a></li>
<li><a href="https://ai-voice-clone.techidaily.com/updated-create-ai-avatar-video-with-avatar-online-for-2024/"><u>Updated Create AI Avatar Video with Avatar | Online for 2024</u></a></li>
</ul></div>

