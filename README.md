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



## Conclusion

In this project, a mini honeynet was constructed in Microsoft Azure and log sources were integrated into a Log Analytics workspace. Microsoft Sentinel was employed to trigger alerts and create incidents based on the ingested logs. Additionally, metrics were measured in the insecure environment before security controls were applied, and then again after implementing security measures. It is noteworthy that the number of security events and incidents were drastically reduced after the security controls were applied, demonstrating their effectiveness.

It is worth noting that if the resources within the network were heavily utilized by regular users, it is likely that more security events and alerts may have been generated within the 24-hour period following the implementation of the security controls.
