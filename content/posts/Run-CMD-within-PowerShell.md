---
author:
  name: "Josh Duffney"
date: 2015-04-10
linktitle: Run CMD Commands within a PowerShell Script
type: post
type: posts
title: Run CMD Commands within a PowerShell Script
aliases: 
- /RunCMD-withinPowerShell
tags: ["PowerShell","CMD","Command Prompt"]
categories: ["how-to"]
---

**Applies to: Windows PowerShell 2.0+**

Sometimes when you enter commands into PowerShell they don't execute the same way as they would in the command prompt. I ran into this issue with an uninstall string for a security software called Cylance Protect. The uninstall string looks like this:

```powershell
msiexec /Lvx* c:\Temp\MsiUnInstall.log /x {2E64FC5C-9286-4A31-916B-0D8AE4B22954} /qn
```

When I executed it within the command prompt it ran as expected, however when executed in PowerShell it pulled up the msi info page. The way I resolved this was by using cmd C\ followed by my uninstall command. The below code demonstrates this. Long story short use cmd /C "Command" to run cmd commands inside a PowerShell script.

# Run CMD commands in PowerShell

```powershell
cmd /c "msiexec /Lvx* c:\Temp\MsiUnInstall.log /x {2E64FC5C-9286-4A31-916B-0D8AE4B22954} /qn"
```

## Filepath has spaces

```powershell
cmd /c "`"C:\Program Files\Sophos\Endpoint Defense\SEDcli.exe`" -TPoff $tamperpassword"
```

Contribution [Gabriel McColl](https://twitter.com/gabrielmccoll)

<br>

---

<div align="center">
<p>"The Most <b>Actionable</b> Newsletter to Hit Your Inbox"</p>
<iframe src="https://duffney.substack.com/embed" width="480" height="320" style="border:1px solid #EEE; background:white;" frameborder="0" scrolling="no"></iframe>
<p><i>No spam. Just the best work I'm capable of.</i></p>
</div>

<br>