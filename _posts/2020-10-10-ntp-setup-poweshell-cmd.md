---
layout: post
title: How to display all object properties in PowerShell
date:   2020-10-13 22:02
categories: powershell
tags: powershell, properties
---

The default way to get the object properties is to use the `Get-Member` cmdlet or it's alias `gm`.

```powershell
Get-AdUser -Filter * | Get-Member
```

![Get-Member](assets/2020-10-13-display-pwsh-properties/gm.png)

But in some cases, not all properties are displayed.

I'm using  `-properties *` parameter to get all parameters displayed.

```powershell
Get-AdUser -Filter * -Properties *| Get-Member
```
![With '-Properties *' parameter](/assets/2020-10-13-display-pwsh-properties/properties-gm.png)

---
