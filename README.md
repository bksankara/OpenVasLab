# Using OpenVas To Mangage and Remediate Vulnerabilities In Azure

<p align="center">
  <img width="460" height="680" src="https://i.imgur.com/myNkVkf.png">
</p>

## Introduction

In this project, I create a vulnerable environment by disabling the firewall and installing very outdated software onto a Windows 10 virtual machine in Microsoft Azure. I then set up a vulnerability scanner on a seperate VM using OpenVas by Greenbone. Next, configurations were made to allow the vunerability scanner to run an uncredentialed scan on our vulnerable machine. Finally, I configured the virtual machines with my login credentials to then alllow for a fully credentialed scan.

Results were analyzed and vulnerabilites were carefully remediated. Remediation success was verified by running a subsequent credentialed scan.

Outdated Software Installed:

- Mozilla Firefox
- Adobe Acrobat
- VLC Media Player

## Architecture Before Hardening / Security Controls
![Architecture Diagram](https://i.imgur.com/yXGrvNQ.png)

## Architecture After Hardening / Security Controls
![Architecture Diagram](https://i.imgur.com/mZ5Yx1k.png)

The architecture of the mini honeynet in Azure consists of the following components:

- Virtual Network (VNet)
- Network Security Group (NSG)
- Virtual Machines (2 windows, 1 linux)
- Log Analytics Workspace
- Azure Key Vault
- Azure Storage Account
- Microsoft Sentinel

For the "BEFORE" metrics, all resources were originally deployed, exposed to the internet. The Virtual Machines had both their Network Security Groups and built-in firewalls wide open, and all other resources are deployed with public endpoints visible to the Internet; aka, no use for Private Endpoints.

For the "AFTER" metrics, Network Security Groups were hardened by blocking ALL traffic with the exception of my admin workstation, and all other resources were protected by their built-in firewalls as well as Private Endpoint

## Attack Maps Before Hardening / Security Controls
![NSG Allowed Inbound Malicious Flows](https://i.imgur.com/DpDSAdI.jpg)<br>
![Linux Syslog Auth Failures](https://i.imgur.com/bwzMFwf.jpg)<br>
![Windows RDP/SMB Auth Failures](https://i.imgur.com/GzhZpat.png)<br>

## Metrics Before Hardening / Security Controls

The following table shows the metrics we measured in our insecure environment for 24 hours:
Start Time 2024-01-04 21:57:53
Stop Time 2024-01-05 21:57:53

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 47117
| Syslog                   | 24446
| SecurityAlert            | 6
| SecurityIncident         | 515
| AzureNetworkAnalytics_CL | 103

## Attack Maps After Hardening / Security Controls

```All map queries returned no results due to no instances of malicious activity for the 24 hour period after hardening.```

## Metrics After Hardening / Security Controls

The following table shows the metrics we measured in our environment for another 24 hours, but after we have applied security controls:
Start Time 2024-01-06 11:31:40
Stop Time	2024-01-07 11:31:40

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 9082
| Syslog                   | 1
| SecurityAlert            | 0
| SecurityIncident         | 0
| AzureNetworkAnalytics_CL | 0

## Conclusion

In this project, a mini honeynet was constructed in Microsoft Azure and log sources were integrated into a Log Analytics workspace. Microsoft Sentinel was employed to trigger alerts and create incidents based on the ingested logs. Additionally, metrics were measured in the insecure environment before security controls were applied, and then again after implementing security measures. It is noteworthy that the number of security events and incidents were drastically reduced after the security controls were applied, demonstrating their effectiveness.

It is worth noting that if the resources within the network were heavily utilized by regular users, it is likely that more security events and alerts may have been generated within the 24-hour period following the implementation of the security controls.
