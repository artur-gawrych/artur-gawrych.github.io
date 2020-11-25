---
layout: post
title: How to Export and Import saved Wi-Fi networks from one device to another.
date:   2020-11-10 11:00
categories: powershell
tags: Wi-Fi, powershell,
---

To see existing Wi-Fi profiles run `netsh wlan show profiles` command.

## Export

```powershell
$FolderPath = "$env:USERPROFILE\Documents\WiFiNetworks"
if (!(Test-Path $FolderPath)) {
    New-Item -Path $FolderPath -ItemType Directory
}
netsh wlan export profile folder="$FolderPath" key=clear
```

## Import

```powershell
$WiFiNetworks = Get-ChildItem "$env:USERPROFILE\Documents\WiFiNetworks" | Select-Object Name
foreach ($network in $WiFiNetworks) {
    netsh wlan add profile filename=$($network.Name) user=all
}
```

---