---
title: "Advanced Settings Screen"
description: "Provides information on the System > Advanced screen, widgets, and configuration screen settings."
weight: 30
aliases: 
 - /scale/scaleuireference/systemsettings/advancedsettings/
tags:
 - scalesettings
 - scalepools
 - scaledisks
 - scaledatasets
 - scalecronjob
 - scaleconsole
 - scalereplication
 - scaleinitshutdown
 - scalegpu
 - scalevms
 - scalesed
 - scale2fa
---

{{< toc >}}

The **Advanced** settings screen provides configuration options for the console, syslog, Kernel, sysctl, replication, cron jobs, init/shutdown scripts, system dataset pool, isolated GPU device(s), self-encrypting drives, sessions, and global two-factor authentication.

{{< trueimage src="/images/SCALE/23.10/SystemAdvancedScreen.png" alt="SCALE Advanced Settings Screen" id="SCALE Advanced Settings Screen" >}}

{{< include file="/_includes/AdvancedSettingsWarningSCALE.md" >}}

**Save Debug** saves a system debug file to the local machine.

## Console Widget

The **Console** widget on the **System Setting > Advanced** screen displays current console settings for TrueNAS.

{{< trueimage src="/images/SCALE/22.12/AdvancedSystemSettingsConsoleWidget.png" alt="Console Widget" id="Console Widget" >}}

**Configure** opens the **[Console](#console-configuration-screen)** configuration screen.

### Console Configuration Screen

**Console** settings configure how the [Console setup menu]({{< relref "ConsoleSetupMenuSCALE.md" >}}) displays, the serial port it uses and the port speed, and the banner users see when accessing it.
{{< expand "Click Here for More Information" "v" >}}

{{< trueimage src="/images/SCALE/22.12/ConsoleConfigScreen.png" alt="Console Config Screen" id="Console Config Screen" >}}

{{< truetable >}}
| Settings | Description |
|----------|-------------|
| **Show Text Console without Password Prompt** | Select to display the console without being prompted to enter a password. Leave empty to add a login prompt to the system before showing the console menu. |
| **Enable Serial Console** | Select to enable the serial console. Do not select this if the serial port is disabled. |
| **Serial Port** | Enter the serial console port address. |
| **Serial Speed** | Select the speed (in bits per second) the serial port uses from the dropdown list. Options are 9600, 19200, 38400, 57600, or 115200. |
| **MOTD Banner** | Enter the message you want to display when a user logs in with SSH. |
{{< /truetable >}}
{{< /expand >}}

## Syslog Widget

The **Syslog** widget displays the existing system logging settings that specify how and when the system sends log messages to the syslog server.

{{< trueimage src="/images/SCALE/23.10/AdvancedSystemSettingsSyslogWidget.png" alt="Syslog Widget" id="Syslog Widget" >}}

**Configure** opens the **[Syslog](#syslog-configuration-screen)** configuration screen.

### Syslog Configuration Screen

The **Syslog** settings specify the logging level the system uses to record system events to the boot device.
There are also options to configure a remote syslog server for recording system events.
{{< expand "Click Here for More Information" "v" >}}

{{< trueimage src="/images/SCALE/23.10/SyslogConfigScreen.png" alt="Syslog Config Screen" id="Syslog Config Screen" >}}

{{< truetable >}}
| Settings | Description |
|----------|-------------|
| **Use FQDN for Logging** | Select to include the fully-qualified domain name (FQDN) in logs to identify systems with similar host names. |
| **Syslog Level** | Select the logging level the syslog server uses when creating system logs; the system only sends logs matching this level. |
| **Syslog Server** | Enter the remote syslog server DNS hostname or IP address. Add a colon and the port number to the hostname to use non-standard port numbers, like *mysyslogserver:1928*. Log entries are written to local logs and sent to the remote syslog server. |
| **Syslog Transport** | Enter the [transport protocol](https://tools.ietf.org/html/rfc8095) for the remote system log server connection. Selecting Transport Layer Security (TLS) displays the **Syslog TLS Certificate** and **Syslog TSL Certificate Authority** fields. This setting requires preconfiguring both the server system certificate and the certificate authority (CA). |
| **Syslog TLS Certificate** | Displays after selecting **TLS** in **Syslog Transport**. Select the [transport protocol](https://tools.ietf.org/html/rfc8095) for the remote system log server TLS certificate from the dropdown list. Select the default or add the certificate and CA for the server using the **Credentials > Certificates** screen **Certificates** widget. |
| **Syslog TLS Certificate Authority** | Displays after selecting **TLS** in **Syslog Transport**. Select the TLS CA for the TLS server from the dropdown list. If not using the default, create the CA for the systlog server TLS certificate on the **Credentials > Certificates > Certificate Authorities** screen. |
{{< /truetable >}}
{{< /expand >}}

## Kernel Widget

The **Kernel** widget shows options for configuring the Linux kernel installed with TrueNAS SCALE.

{{< trueimage src="/images/SCALE/23.10/SystemSettingsAdvancedKernel.png" alt="Kernel Widget" id="Kernel Widget" >}}

{{< expand "Click Here for More Information" "v" >}}
{{< truetable >}}
| Settings | Description |
|----------|-------------|
| **Enable Debug Kernel** | Set to boot a debug kernel after the next system reboot. |
{{< /truetable >}}
{{< /expand >}}

## Cron Jobs Widget

The **Cron Jobs** widget displays **No Cron Jobs configured** until you add a cron job, then it shows the information on cron job(s) configured on the system.

{{< trueimage src="/images/SCALE/23.10/AdvancedSettingsCronJobWidget.png" alt="Cron Job Widget" id="Cron Job Widget" >}}

**Add** opens the **[Add Cron Job](#add-or-edit-cron-job-configuration-screen)** configuration screen.
Click on any job listed in the widget to open the **[Edit Cron Jobs](#add-or-edit-cron-job-configuration-screen)** configuration screen populated with the settings for that cron job.

### Add or Edit Cron Job Configuration Screen

The **Add Cron Job** and **Edit Cron Job** configuration screens display the same settings. **Cron Jobs** lets users configure jobs that run specific commands or scripts on a regular schedule using [cron(8)](https://manpages.debian.org/testing/cron/cron.8.en.html "Cron Man Page"). Cron jobs help users run repetitive tasks.
{{< expand "Click Here for More Information" "v" >}}

{{< trueimage src="/images/SCALE/23.10/AddCronJobScreen.png" alt="Add Cron Job Screen" id="Add Cron Job Screen" >}}

{{< truetable >}}
| Settings | Description |
|----------|-------------|
| **Description** | Enter a description for the cron job. |
| **Command** | Enter the full path to the command or script to run. For example, to create a command string that generates a list of users on the system and write that list to a file, enter `cat /etc/passwd > users_$(date +%F).txt`  |
| **Run As User** | Select a user account to run the command. The user must have permissions allowing them to run the command or script. |
| **Schedule** | Select a schedule preset or choose **Custom** to open the advanced scheduler. Note that an in-progress cron task postpones any later scheduled instance of the same task until the running task is complete. |
| **Hide Standard Output** | Select to hide standard output (stdout) from the command. If left cleared, TrueNAS mails any standard output to the user account cron that ran the command. |
| **Hide Standard Error** | Select to hide error output (stderr) from the command. If left cleared, TrueNAS mails any error output to the user account cron that ran the command. |
| **Enabled** | Select to enable this cron job. Leave cleared to disable the cron job without deleting it. |
{{< /truetable >}}
{{< /expand >}}

## Init/Shutdown Scripts Widget

The **Init/Shutdown Scripts** widget displays **No Init/Shutdown Scripts configured** until you add either a command or script, then the widget lists the scrips configured on the system.

{{< trueimage src="/images/SCALE/23.10/AdvancedSystemInitShutdownScriptWidget.png" alt="Init/Shutdown Scripts Widget" id="Init/Shutdown Scripts Widget" >}}

**Add** opens the **[Add Init/Shutdown Script](#add-or-edit-initshutdown-script-configuration-screens)** configuration screen.
Any script listed is a link that opens the **[Edit Init/Shutdown Script](#add-or-edit-initshutdown-script-configuration-screens)** configuration screen populated with the settings for that script.

### Add or Edit Init/Shutdown Script Configuration Screens

**Init/Shutdown Scripts** lets users schedule commands or scripts to run at system startup or shutdown.
{{< expand "Click Here for More Information" "v" >}}

{{< trueimage src="/images/SCALE/22.12/AddInitShutdownScriptConfigScreen.png" alt="Add Init/Shutdown Scripts" id="Add Init/Shutdown Scripts" >}}

{{< truetable >}}
| Settings | Description |
|----------|-------------|
| **Description** | Comments about this script. |
| **Type** | Select *Command* for an executable or *Script* for an executable script. |
| **Command** | Enter the command with any options. |
| **Script** | Select the script. The script runs using [dash(1)](https://manpages.debian.org/testing/dash/sh.1.en.html "dash(1) Page"). |
| **When** | Select when the command or script runs from the dropdown list. Options are **Pre Init** for early in the boot process, after mounting file systems and starting networking. **Post Init** runs at the end of the boot process before Linux services start. **Shutdown** runs during the system power-off process. |
| **Enabled** | Select to enable this script. When left cleared, it disables the script without deleting it. |
| **Timeout** | Automatically stop the script or command after the specified number of seconds. |
{{< /truetable >}}
{{< /expand >}}

## Sysctl Widget

The **Sysctl** widget displays either **No Sysctl configured** or the existing sysctl settings on the system.

{{< trueimage src="/images/SCALE/23.10/AdvancedSysctlWidget.png" alt="Sysctl Widget" id="Sysctl Widget" >}}

**Add** to add a tunable that configures a kernel module parameter at runtime.

### Add or Edit Sysctl Configuration Screen

The **Add Sysctl** or **Edit Sysctl** configuration screen settings let users set up tunables that configure kernel parameters at runtime.
{{< expand "Click Here for More Information" "v" >}}

{{< trueimage src="/images/SCALE/22.12/AddSysctlConfigScreen.png" alt="Sysctl Config Screen" id="Sysctl Config Screen" >}}

{{< truetable >}}
| Settings | Description |
|----------|-------------|
| **Variable** | Enter the name of the sysctl variable to configure. Sysctl tunables configure kernel parameters while the system runs and generally take effect immediately. |
| **Value** | Enter a [sysctl](https://man7.org/linux/man-pages/man8/sysctl.8.html) value to use for the loader, **sysctl** variable. |
| **Description** | Enter a description for the tunable. |
| **Enabled** | Select to enable this tunable. Leave clear to disable this tunable without deleting it. |
{{< /truetable >}}
{{< /expand >}}

## Storage Widget

**Storage** widget displays the pool configured as the system dataset pool and allows users to select the storage pool they want to hold the system dataset.
The system dataset stores core files for debugging and keys for encrypted pools. It also stores Samba4 metadata, such as the user and group cache and share-level permissions.

{{< trueimage src="/images/SCALE/22.12/AdvancedSystemStorageWidget.png" alt="Storage Widget" id="Storage Widget" >}}

**Configure** opens the **Storage Settings** configuration screen.

### Storage Settings Configuration Screen

If the system has one pool, TrueNAS configures that pool as the system dataset pool. If your system has more than one pool, you can set the system dataset pool using the **Select Pool** dropdown. Users can move the system dataset to an unencrypted pool, or an encrypted pool without passphrases.

{{< trueimage src="/images/SCALE/22.12/SystemStorageConfigScreen.png" alt="System Dataset Pool Config Screen" id="System Dataset Pool Config Screen" >}}

Users can move the system dataset to a key-encrypted pool, but cannot change the pool encryption type afterward. If the encrypted pool already has a passphrase set, you cannot move the system dataset to that pool.

**Swap Size** lets users enter an amount (in GiB) of hard disk space to use as a substitute for RAM when the system fully utilizes the actual RAM.

By default, the system creates all data disks with the specified swap amount. Changing the value does not affect the amount of swap on existing disks, only disks added after the change. Swap size does not affect log or cache devices.

## Replication Widget

The **Replication** widget displays the number of replication tasks that can execute simultaneously configured on the system. It allows users to adjust the maximum number of replication tasks the system can perform simultaneously.

{{< trueimage src="/images/SCALE/23.10/SystemAdvancedSettingsReplicationWidget.png" alt="Replication Widget" id="Replication Widget" >}}

Click **Configure** to open the **Replication** configuration screen.

{{< trueimage src="/images/SCALE/23.10/AdvancedSettingsReplicationConfigScreen.png" alt="Replication Config Screen" id="Replication Config Screen" >}}

Enter a number for the maximum number of simultaneous replication tasks you want to allow the system to process and click **Save**.

## Sessions Widget

The **Sessions** widget displays a list of all active sessions, including the user who initiated the session and what time it started.
It also displays the **Token Lifetime** setting for your current session.
It allows administrators to manage other active sessions and to configure the token lifetime for their account.

{{< trueimage src="/images/SCALE/23.10/AdvancedSystemSettingsSessionsWidget.png" alt="Sessions Widget" id="Sessions Widget" >}}

The **Terminate Other Sessions** button ends all sessions except for the one you are currently using.
You can also end individual sessions by clicking the logout <span class="iconify" data-icon="bi:box-arrow-in-right"></span> button next to that session.
You must check a confirmation box before the system allows you to end sessions.

The logout button is inactive for your current session and active for all other current sessions.
It cannot be used to terminate your current session.

**Token Lifetime** displays the configured token duration for your current session (default five minutes).
TrueNAS SCALE logs out user sessions that are inactive for longer than that user's configured token setting.
New activity resets the token counter.

If the configured token lifetime is exceeded, TrueNAS SCALE displays a **Logout** dialog with the exceeded ticket lifetime value and the time that the session is scheduled to terminate.

{{< expand "Logout Dialog" "v" >}}
{{< trueimage src="/images/SCALE/23.10/TimeoutDialog.png" alt="Logout Dialog" id="Logout Dialog" >}}

**Extend Session** resets the token counter.
If the button is not clicked, the TrueNAS SCALE terminates the session automatically and returns to the log in screen.
{{< /expand >}}

 **Configure** opens the **Token Settings** screen.

### Token Settings Screen

The **Token Settings** screen allows users to configure the **Token Lifetime** for the current account.

{{< expand "" "v" >}}
{{< trueimage src="/images/SCALE/23.10/TokenSettingsScreen.png" alt="Token Settings Screen" id="Token Settings Screen" >}}

Select a value that fits your needs and security requirements.
Enter the value in seconds.

{{< hint type=tip >}}
The default lifetime setting is 300 seconds, or five minutes.

The maximum is 2147482 seconds, or 20 hours, 31 minutes, and 22 seconds.
{{< /hint >}}
{{< /expand >}}

## Self-Encrypting Drive Widget

The **Self-Encrypting Drive** (SED) widget displays the system ATA security user and password.

{{< trueimage src="/images/SCALE/23.10/AdvancedSystemSEDWidget.png" alt="Self-Encrypting Drive Widget" id="Self-Encrypting Drive Widget" >}}

**Configure** opens the **[Self-Encrypting Drive](#self-encrypting-drive-configuration-screen)** configuration screen.

### Self-Encrypting Drive Configuration Screen

The **Self-Encrypting Drive** configuration screen allows users to set the ATA security user and create a SED global password.
{{< expand "Click Here for More Information" "v" >}}

{{< trueimage src="/images/SCALE/23.10/AdvancedSystemSelfEncryptingDriveConfigScreen.png" alt="Self-Encrypting Drive Config Screen" id="Self-Encrypting Drive Config Screen" >}}

{{< truetable >}}
| Settings | Description |
|----------|-------------|
| **ATA Security User** | Select the user passed to `camcontrol security -u` to unlock SEDs from the dropdown list. Options are **USER** or **MASTER**. |
| **SED Password** | Enter the global password to unlock SEDs. |
| **Confirm SED Password** | Re-enter the global password to unlock SEDs. |
{{< /truetable >}}
{{< /expand >}}

## Isolated GPU Device(s) Widget

The **Isolated GPU Device(s)** widget displays any isolated graphics processing unit (GPU) device(s) configured on your system.

{{< trueimage src="/images/SCALE/23.10/AdvancedSettingIsolatedGPUDeviceWidget.png" alt="Isolated GPU Device Widget" id="Isolated GPU Device Widget" >}}

**Configure** opens the **Isolate GPU PCI's ID** screen, which allows users to isolate additional GPU devices.

### Isolate GPU PCI's ID Configuration Screen

The **Isolate GPU PCI's ID** configuration screen allows you to isolate GPU devices for a virtual machine (VM) or applications.

{{< expand "Click Here for More Information" "v" >}}
To isolate a GPU, you must have at least two in your system; one allocated to the host system for system functions and the other available to isolate for use by either a VM or applications.
It is possible for some specific GPUs to allocate individual cores between the operating system and applications, but this is highly hardware dependent.

{{< trueimage src="/images/SCALE/23.10/IsolatedGPUPCIIDsConfigScreen.png" alt="Isolated GPU PCI Ids Screen" id="Isolated GPU PCI Ids Screen" >}}

Select the GPU device ID from the dropdown list and click **Save**.

Isolated GPU devices are reserved for use by configured applications or a VM.

To allocate an isolated GPU device, select it while creating or editing VM configuration, in the **GPU Configuration** settings of individual applications that support GPU allocation, or in the **Resource Reservation** settings of [**Install Custom App**]({{< relref "InstallCustomAppScreens.md" >}}).
When allocated to a VM, the isolated GPU connects to the VM as if it were physically installed in that VM and becomes unavailable for any other allocations.
One isolated GPU device can be used by a single VM or multiple applications, but not both.
{{< /expand >}}

## Global Two Factor Authentication Widget

The **Global Two Factor Authentication** widget allows you to set up two factor authentication (2FA) for your system.

{{< trueimage src="/images/SCALE/23.10/GlobalTwoFactorAuthenticationWidget.png" alt="Global Two Factor Authentication Widget" id="Global Two Factor Authentication Settings Widget" >}}

**Configure** opens the **Global Two Factor Authentication Settings** configuration screen.

{{< expand "Click Here for More Information" "v" >}}

{{< trueimage src="/images/SCALE/23.10/GlobalTwoFactorAuthenticationSettingsScreen.png" alt="Global Two Factor Authentication Settings Screen" id="Global Two Factor Authentication Settings Screen" >}}

{{< truetable >}}
| Name | Description |
|------|-------------|
| **Enable Two-Factor Authentication Globally** | Select to enable 2FA for the system. |
| **Interval (in seconds)** | Enter the number of seconds for the lifespan of each OTP. The default is **30** seconds. The minimum is 5 seconds. |
| **Window** | Enter the number of valid passwords. Extends password validity beyond the **Interval** setting. For example, *1* means that one password before and after the current password is valid, leaving three valid passwords. Extending the window is useful in high-latency situations. |
| **One Time Password (OTP) Digits** | Select the number of digits for the length of the one-time password (OTP). The default is **6**, which is the standard OTP length for Google OTPs. Check your app/device settings before selecting a value. |
| **Enable Two-Factor Auth for SSH** | Select to enable 2FA for system SSH access. Leave this disabled until you complete a successful test of 2FA with the UI. |
{{< /truetable >}}
{{< /expand >}}

{{< taglist tag="scalesettings" limit="10" >}}