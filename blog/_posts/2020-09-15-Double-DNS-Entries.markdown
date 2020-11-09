---
layout: post
title:  "Double DNS Entries From Your HP ProLiant Server?"
date:   2020-09-15
---
Do you have an HP ProLiant DL 180 Gen10 server running Windows Server OS? Are you seeing double entries for the server domain name in your DNS records that are causing client connection issues (*i.e. one entry with the correct IP and a second with an incorrect 16.1.x.x IP*)? 

Some versions of the HP ProLiant DL 180 Gen10 server come with a built-in "Generic USB-EEM Network Adapter" that will report a problematic second IP address to DNS. If you are not using the adapter, disable it by going into "Network and Sharing Center" then "Network Connections", right click the "Generic USB-EEM Network Adapter", and select "Disable" OR use the Powershell one-liner below to disable it:

```powershell
Get-NetAdapter | Where-Object {$_.InterfaceDescription -eq "Generic USB-EEM Network Adapter"} | Disable-NetAdapter
```
