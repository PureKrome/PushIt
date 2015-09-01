# Push It

- Powershell script
- Very simple to package and deploy _multiple_ `nuspec` files at the same time.
- Ability to deploy locally (ie. copy files) to test your packages before publishing
- Because it's a powershell script, it's easy to integrate with AppVeyor.

![](http://i.giphy.com/OQORmsNpzwqlO.gif)

![](http://i.imgur.com/lI4qvNl.gif)

# How do I do this / use this powershell script?
This package is just a powershell script, so you need to run the package/push command to do all the heavy lifting for you. So how do I get this :sparkles: script :sparkles: ?

- Install (this) NuGet package
- Create `nuspec` file(s)
- Execute powershell command.
- :moneybags: :moneybags: :moneybags:

![install-package PureKrome.PushIt](http://i.imgur.com/cmt4uxJ.png)
- `install-package PureKrome.PushIt`

Installing this nuget package just does 1 thing => it downloads the powershell script and stores it in a folder called `NuGet` in your `root` directory of your application. **That's It**.

Next, we need a `nuspec` file. So create 1 or 3 or 1000 of those file(s) and stick them anywhere. _Personally_ i would stick it in the `\NuGet` folder (side by side to this powershell script).

Last, we execute our powershell script to do the package/publishing.
 
---
# Cheat Sheat
NOTE: 
- _P/P_ means package/publish...
- _file.ps_ is the name of the script that was downloaded. The default name is `NuGet Package and Package.ps1` but that's pretty long/verbose for this help/FAQ so we'll shorten it, here :)

Scenario: I'm creating a NuGet package so I need to do heaps of testing before I publish it up to the interwebs.  
Answer: P/P locally to some folder and then use Visual Studio to use that folder as a NuGet repository!
- `& '.\file.ps1' -nuget c:\temp\nuget.exe -destination c:\temp\nugets -version 0.1-alpha`

Scenario: I'm still doing some localhost development (so the packages shouldn't go up to the interwebs) but my nuspecs are now in a _different_ folder (no .. don't ask why... just accept this)  
Answer: Same answer as above but define the source directory
- `& '.\file.ps1' -nuget c:\temp\nuget.exe -destination c:\temp\nugets -source ..\anotherFolder\turtles\all\the\way\down -version 0.1-alpha`

Scenario: Ok, so far so good. I'm ready to test stuff. But ... I want to push it up to MyGet (not the official NuGet and yes, I know that there's the `-pre` option but I'm not using that, yet).  
Answer: Sure can. You'll need to get your MyGet feed Url -and- ApiKey. Once you have that ...
- `& '.\file.ps1' -nuget c:\temp\nuget.exe -destination c:\temp\nugets -feedSource https://www.myget.org/F/<BlahBlahBlah>/api/v2 -apiKey ABCD-EFG...`

Scenario: Push It!! Time to go live, peeps! Show me the money! (read: Lets publish this to the official servers @ NuGet.org)  
Answer: Time for the money-shot.
- `& '.\file.ps1' -nuget c:\temp\nuget.exe -destination c:\temp\nugets -apiKey ABCD-EFG...`


---
[![I'm happy to accept tips](http://img.shields.io/gittip/purekrome.svg?style=flat-square)](https://gratipay.com/PureKrome/)  
![Lic: MIT](http://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)

