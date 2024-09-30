---
title: Unlock Seamless File Transformation with PowerShell and Visual Basic Scripts
date: 2024-09-25T17:26:36.051Z
updated: 2024-09-29T21:15:37.761Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: This Article Describes Unlock Seamless File Transformation with PowerShell and Visual Basic Scripts
thumbnail: https://thmb.techidaily.com/99e083d06891d6b9709e3f748eff8a9d6ada1ef3054d20b60fdb2ab68b2e719b.png
---

## Unlock Seamless File Transformation with PowerShell and Visual Basic Scripts

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Dehardcode within files

Often throughout the repackaging process, it's frequent to come across files featuring straightforward paths such as: _C:\\Program Files_.

Allowing users to modify the installation path of their application is a common practice. However, this practice comes with one downside: the need to change the path written in those particular files during the installation.

In this article, we'll see how we can replace hard coded paths or variables inside files using custom actions.

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2075472/7443" target="_top" id="2075472">
  <img src="//a.impactradius-go.com/display-ad/7443-2075472" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2075472/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### How to Discover Hard-coded Files?

Before we actually replace the hard coded paths, we first need to find out which files contain hard-coded paths. There are various ways to get this information, but the most straightforward one is to use Notepad++.

For instance, let’s imagine we have an application installed in _C:\\Program Files\\MyApp_. As a general rule, when repackaging, we always search for the **installation directory inside all of the application files**.

In this scenario, the installer sets the [ProgramFilesFolder](https://learn.microsoft.com/en-us/windows/win32/msi/programfilesfolder "ProgramFilesFolder") property to the full path of the Program Files folder. So we don’t need to search for the full _C:\\Program Files\\MyApp_ string, only for the part that we can use as a variable - in our case, the _C:\\Program Files\\_ string.

![Tip](https://cdn.advancedinstaller.com/svg/common/IconMessageTip.svg)Keep in mind that the “Program Files” is an internal property known by the MSI.

Other properties include [AppDataFolder](https://learn.microsoft.com/en-us/windows/win32/msi/appdatafolder "AppDataFolder"), [CommonAppDataFolder](https://learn.microsoft.com/en-us/windows/win32/msi/commonappdatafolder "CommonAppDataFolder"), [CommonFiles64Folder](https://learn.microsoft.com/en-us/windows/win32/msi/commonfiles64folder "CommonFiles64Folder"), [CommonFilesFolder](https://learn.microsoft.com/en-us/windows/win32/msi/commonfilesfolder "CommonFilesFolder"), [DesktopFolder](https://learn.microsoft.com/en-us/windows/win32/msi/desktopfolder "DesktopFolder"), [FontsFolder](https://learn.microsoft.com/en-us/windows/win32/msi/fontsfolder "FontsFolder"), [LocalAppDataFolder](https://learn.microsoft.com/en-us/windows/win32/msi/localappdatafolder "LocalAppDataFolder"), [MyPicturesFolder](https://learn.microsoft.com/en-us/windows/win32/msi/mypicturesfolder "MyPicturesFolder"), [PersonalFolder](https://learn.microsoft.com/en-us/windows/win32/msi/personalfolder "PersonalFolder"), [PrimaryVolumePath](https://learn.microsoft.com/en-us/windows/win32/msi/primaryvolumepath "PrimaryVolumePath"), [ProgramFiles64Folder](https://learn.microsoft.com/en-us/windows/win32/msi/programfiles64folder "ProgramFiles64Folder"), [ProgramMenuFolder](https://learn.microsoft.com/en-us/windows/win32/msi/programmenufolder "ProgramMenuFolder"), [StartMenuFolder](https://learn.microsoft.com/en-us/windows/win32/msi/startmenufolder "StartMenuFolder"), [System64Folder](https://learn.microsoft.com/en-us/windows/win32/msi/system64folder "System64Folder"), [SystemFolder](https://learn.microsoft.com/en-us/windows/win32/msi/systemfolder "SystemFolder"), [TempFolder](https://learn.microsoft.com/en-us/windows/win32/msi/tempfolder "TempFolder"), [WindowsFolder](https://learn.microsoft.com/en-us/windows/win32/msi/windowsfolder "WindowsFolder") and [WindowsVolume](https://learn.microsoft.com/en-us/windows/win32/msi/windowsvolume "WindowsVolume"). By using one of these properties, we can de-hardcode part of the installation directory as a best practice.

To see which files contain the C:\\Program Files\\path, follow these steps:

1\. Open Notepad++ and go to **Search** \> **Find in Files**.

![Find in files](https://cdn.advancedinstaller.com/img/dehardcode-file-paths-with-custom-actions/findinfiles.png "Find in files")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1918703/19272" target="_top" id="1918703">
  <img src="//a.impactradius-go.com/display-ad/19272-1918703" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1918703/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

2\. In the **Find What** field, input the INSTALLDIR of your application, in our case: C:\\Program Files\\.

3\. In the **Directory** field, input the location of your captured files.

4\. Then, click on **Find All**.

If there are any matches found, Notepad++ will show you at what **file and line** you can find the string.

![Find in files result](https://cdn.advancedinstaller.com/img/dehardcode-file-paths-with-custom-actions/findinfilesresult.png "Find in files result")  

<!-- affiliate ads begin -->
<a href="https://wigfever.sjv.io/c/5597632/2005184/22899" target="_top" id="2005184">
  <img src="//a.impactradius-go.com/display-ad/22899-2005184" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://wigfever.sjv.io/i/5597632/2005184/22899" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### How Does Automatic INI De-hardcoding Work?

As you can see from above, Notepad++ found our location inside an INI file. However, working with INI files becomes a straightforward process when using Advanced Installer. During the repackaging process, the Advanced Installer imports all INI files into the project and **de-hardcodes them automatically**.

Additionally, when you add a new INI file while editing your project, Advanced Installer easily identifies potential variables and automatically de-hardcodes the file.

Want to see Advanced Installer in action? Check it out through our [30-day full featured free trial](https://tools.techidaily.com/advancedinstaller/products/) and elevate your installation process today!

![AI Ini](https://cdn.advancedinstaller.com/img/dehardcode-file-paths-with-custom-actions/AIIni.png "AI Ini")  

### De-hardcoding Files Using VBScript Custom Actions

When it comes to other types of files, we must perform additional steps to de-hardcode the locations we need. In this case, we’ll use the MSI's custom actions capability. 

For **VBScript Custom Actions**, you can use the following script:

'On Error Resume Next
'Option Explicit
Const ForReading = 1, ForWriting = 2, ForAppending = 8
Dim strFilePath, strToReplace, strNewValue, path1, path2
strArgs = Session.Property("CustomActionData")
arrArgs = Split(strArgs, ";", -1, 1)
path1 = arrArgs(0)
path2 = arrArgs(1)
Function ReplaceInFile(strToReplace, strNewValue, strFilePath)
    Dim objFSO, objFile, strText, re
    Set objFSO = CreateObject("Scripting.FileSystemObject")
    if objFSO.FileExists(strFilePath) Then
   	 Set objFile = objFSO.OpenTextFile(strFilePath, ForReading, True)
   		 strText = objFile.ReadAll
   	 objFile.Close
   	 Set objFile = Nothing
   	 strText = Replace(strText, strToReplace, strNewValue, 1, -1, 0)
   	 Set objFile = objFSO.CreateTextFile(strFilePath, True)
   	 objFile.Write strText
   	 objFile.Close
   	 Set objFile = Nothing
    End If
    Set objFSO = Nothing
End Function
strToReplace = "C:\Program Files\"
strNewValue = path1
ReplaceInFile strToReplace, strNewValue, path2 & "hello.cfg"

Copy

The script is quite long, so let’s try to understand what it does.

Up to line 8, we are using **Session.Property("CustomActionData");** this allows VBScript to catch any arguments passed to it.

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)Check out our article and learn [How to set an installer property using custom actions](https://tools.techidaily.com/advancedinstaller/products/).

<!-- affiliate ads begin -->
<a href="https://laganoo.pxf.io/c/5597632/1484910/16446" target="_top" id="1484910">
  <img src="//a.impactradius-go.com/display-ad/16446-1484910" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://laganoo.pxf.io/i/5597632/1484910/16446" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

At line 9, the "**;**" separates the parameters, and **path1** represents the first argument. The **path2** represents the second argument that we pass.

Next, we can see the **ReplaceInFile** function, which takes the following arguments:

* **strToReplace** \- the string we want to replace.
* **strNewValue** \- the new value we want to add.
* **strFilePath** \- the file path where we want to do the replacement.

The function opens the file mentioned in the **strFilePath** and parses all the text via **objFile.ReadAll**.

Then, we use the [Replace](https://ss64.com/vb/replace.html "Replace") function to replace the string. We can write it in the file with **objFile.Write strText** and close the file with **objFile.Close**. After that, we can dispose of the object with **Set objFile = Nothing**.

The values for **strToReplace** and **strNewValue** are defined below the function. Lastly, we call the function to perform the actions with **ReplaceInFile strToReplace, strNewValue, path2 & "hello.cfg"**_._

Now that we have our script ready, let’s **create the Custom Action** in Advanced Installer and run it. For this, follow the next steps:

1. Navigate to the _Custom Actions Page_.
2. Search for the _Launch attached file_ custom action and add it to the sequence.
3. Select the _VBScript_ that we created previously.
4. In the _Action Data_ field, we need to add the proper variables. Remember, the first one is the string we want to replace **C:\\Program Files\\** with, and the second one is the location where the **hello.cfg** file can be found. For this example, we created an additional property called MYPROPERTY which only contains a string.
5. Since the action is set to _Immediately_ as the Execution Time, we will place it after the _Finish Execution_ stage.
6. Build and install your package.

![AIDehardCA](https://cdn.advancedinstaller.com/img/dehardcode-file-paths-with-custom-actions/AIDehardCA.png "AIDehardCA")  

After the package is installed, if we check the **hello.cfg** file in the INSTALLDIR, we can see that it has been successfully de-hardcoded.

![cfgdehard](https://cdn.advancedinstaller.com/img/dehardcode-file-paths-with-custom-actions/cfgdehard.png "cfgdehard")  

### De-hardcoding Files using PowerShell Custom Actions

With **PowerShell**, the code is much cleaner, shorter, and easier to understand:

$propValue = AI_GetMsiProperty MYPROPERTY
$propDir = AI_GetMsiProperty APPDIR
$fileDir = $propDir + "hello.cfg"
$content = [System.IO.File]::ReadAllText($fileDir).Replace("C:\Program Files\",$propValue)
[System.IO.File]::WriteAllText($fileDir, $content)

Copy

First, we use the [AI\_GetMsiProperty](https://tools.techidaily.com/advancedinstaller/products/) to retrieve our two properties that we used for VBScript, and define the file directory.

Next, we read all the files and replace everything we find as _C:\\Program Files\\_ in it with our property value then write all the text back in.

To add the PowerShell script in Advanced Installer:

1. Navigate to the _Custom Actions Page_.
2. Search for the **Run PowerShell script file** and add it to the sequence.
3. Click **Attached script** and select the file created above.
4. Place the sequence last after the **Finish Execution**.
5. Build and run the installation.

![AIDehardPS](https://cdn.advancedinstaller.com/img/dehardcode-file-paths-with-custom-actions/AIDehardPS.png "AIDehardPS")  

The behavior is the same as with VBScript, and the **hello.cfg** file is correctly de-hardcoded.

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
<li><a href="https://some-approaches.techidaily.com/updated-the-virtual-stage-enhancement-zooms-filter-guidebook/"><u>[Updated] The Virtual Stage Enhancement Zoom's Filter Guidebook</u></a></li>
<li><a href="https://fox-hovers.techidaily.com/2024-approved-untangling-aerial-vehicles-a-guide-to-drones-operation/"><u>2024 Approved Untangling Aerial Vehicles A Guide to Drones' Operation</u></a></li>
<li><a href="https://tech-hub.techidaily.com/can-interaction-shape-the-knowledge-base-of-chatgpt-from-conversations/"><u>Can Interaction Shape the Knowledge Base of ChatGPT From Conversations?</u></a></li>
<li><a href="https://buynow-info.techidaily.com/explore-the-apple-m4-processor-released-information-exciting-features-and-capabilities/"><u>Explore the Apple M4 Processor: Released Information, Exciting Features & Capabilities</u></a></li>
<li><a href="https://extra-information.techidaily.com/humorous-editing-apps-and-tools-a-comprehensive-list-iosandroid/"><u>Humorous Editing Apps & Tools A Comprehensive List (iOS/Android)</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/pchulu-youtube/"><u>PCによるHulu映像のビデオ録画手引き - YouTubeで見る方法</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/step-by-step-strategies-for-archiving-irretrievable-tiktok-footage/"><u>Step-by-Step Strategies for Archiving Irretrievable TikTok Footage</u></a></li>
<li><a href="https://win-dash.techidaily.com/the-us-national-biocontainment-facilities-such-as-the-nihs-rocky-mountain-laboratories-play-a-critical-role-in-researching-dangerous-pathogens-under-high-le43/"><u>The U.S. National Biocontainment Facilities, Such as the NIH's Rocky Mountain Laboratories, Play a Critical Role in Researching Dangerous Pathogens Under High-Level Containment Conditions.</u></a></li>
<li><a href="https://vimeo-videos.techidaily.com/the-ultimate-guide-to-video-excellence-and-staff-picks-at-vimeo-for-2024/"><u>The Ultimate Guide to Video Excellence & Staff Picks at Vimeo for 2024</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/top-techniques-to-stream-wma-files-on-your-android-device/"><u>Top Techniques to Stream WMA Files on Your Android Device</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/ultimate-techniques-for-ripping-burning-and-cloning-data-on-dvds-and-cds/"><u>Ultimate Techniques for Ripping, Burning & Cloning Data on DVDs and CDs</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/vbr-vs-cbr-choosing-the-right-video-compression-method/"><u>VBR vs CBR: Choosing the Right Video Compression Method</u></a></li>
<li><a href="https://win-exclusive.techidaily.com/win-the-new-wonderfox-collection-free-prize-and-special-deals-for-back-to-school-season-2014/"><u>Win the New WonderFox Collection – Free Prize & Special Deals for Back to School Season, 2014!</u></a></li>
</ul></div>

