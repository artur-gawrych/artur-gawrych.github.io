---
layout: post
title: How to setup NTP server in Windows using Powershell / CMD
date:   2020-10-10 21:38
categories: powershell
tags: ntp, windows, cmd, time server,
---

First, stop the time service.
```powershell
net stop w32time
```

Next, add the NTP servers. NTP Sever pool can be found here - <https://www.ntppool.org>
```powershell
w32tm /config /syncfromflags:manual /manualpeerlist:"0.it.pool.ntp.org 1.ie.pool.ntp.org 2.ie.pool.ntp.org 3.ie.pool.ntp.org"
```

After you add the servers start the service,
```powershell
net start w32time
```

update the config,
```powershell
w32tm /config /update
```

 and sync the time.
```powershell
w32tm /resync /rediscover
```

![](/assets/2020-10-10-ntp-setup-poweshell-cmd/ntp-cmd.png)

{:.image-caption}
*Output*

---