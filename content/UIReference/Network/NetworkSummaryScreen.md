---
title: "Network Summary Screen"
description: "Describes the fields in the Network Summary screen in TrueNAS CORE."
weight: 10
tags:
- corenetworksummary
- corenetworkinterfaces
---

It is recommended to set up your system connections before setting up data sharing.
This allows integrating TrueNAS into your specific security and network environment before attempting to store or share critical data.

## Network Summary

The Network Summary gives a concise overview of the current network setup.
Information about the currently active **Interfaces**, **Default Routes**, and **Nameservers** is provided.
These areas are not editable.

![**NetworkSummaryScreen**](/images/CORE/13.0/NetworkSummaryScreen.png "Network Summary Screen")

* [**Interfaces**]({{< relref "/UIReference/Network/InterfacesScreen.md" >}}) shows any configured physical [bridge]({{< relref "/CORETutorials/Network/Interfaces/BridgeCreate.md" >}}), [LAGG]({{< relref "/CORETutorials/Network/Interfaces/LAGGCreate.md" >}}), and [vlan]({{< relref "/CORETutorials/Network/Interfaces/VLANCreate.md" >}}) interfaces.
All detected physical interfaces are listed, even when unconfigured.
The IPv4 or IPv6 address displays when a [static IP]({{< relref "/CORETutorials/Network/Interfaces/SettingStaticIP.md" >}}) is saved for an interface.

* **Default Routes** lists all saved TrueNAS Default Routes.
  Go to **Network > Global Configuration** to configure Default Routes.

* **Nameservers** lists any configured DNS name servers that TrueNAS uses. To change this list, go to **Network > Global Configuration**. 
  The TrueNAS **Hostname and Domain**, **Default Gateway**, and other options are available in **Network > Global Configuration**.

## Additional Network Configuration Screens

Define any Static Routes in **Network > [Static Routes]({{< relref "/UIReference/Network/StaticRoutesScreen.md" >}})**.

Out-of-band management is managed from **Network > [IPMI]({{< relref "/CORETutorials/Network/IPMI.md" >}})**. This option is visible only when TrueNAS detects the appropriate physical hardware.

{{< taglist tag="corenetworkinterfaces" limit="10" >}}