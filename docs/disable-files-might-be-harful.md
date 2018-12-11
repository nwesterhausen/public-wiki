---
title: Disable 'These Files Might Harm Your Computer'
summary: Disabling the warning when you map a network drive.
authors:
    - Nick Westerhausen @nwesterhausen
date: 2018-11-23
---

This error can happen when you mount a network drive in Windows 7/8/10
when you try to perform an operation on files or folders on the mounted drive.

To disable, follow these instructions:

1. Bring up the start menu
2. Type **Internet Options**
3. Open Internet Options
4. Go to the *Security* tab
5. Select *Local intranet* to modify LAN Network settings
6. Click the *Sites* button
7. Click *Advanced* on the window that opens up
8. Here you add exceptions. You can either add the exact IP address of your file
server (recommended) or add an exception for your entire LAN network.

    a. To add an exception that covers multiple hosts, use a star `*` wildcard.
    
    For 192.168.1.1/24 you would put 192.168.1.*
    
9. After adding the server in this menu, click Close and click OK
10. You will have to disconnect and reconnect to the file server before the trust
is realized.


---

Reference article on [tekrevue.com](https://www.tekrevue.com/tip/these-files-might-be-harmful-to-your-computer-disable/)