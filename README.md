# Building a SOC + Honeynet in Azure (Live Traffic)
![Cloud SOC](https://github.com/user-attachments/assets/ad9bf6b8-31cd-4fbf-ab7b-39907bbbf5c8)

## Overview

This project implements a comprehensive Security Information and Event Management (SIEM) system in Microsoft Azure, along with a mini honeynet designed to capture real-world attacker traffic. The honeynet is exposed to the internet for 24 hours, allowing for the ingestion of log sources into a Log Analytics workspace, where Microsoft Sentinel is used to build attack maps, trigger alerts, and create incidents.

After measuring security metrics in an insecure environment, security controls based on NIST 800-61 Incident Response and NIST 800-53 Security Controls are applied to harden the environment. A subsequent 24-hour monitoring phase evaluates the effectiveness of these enhancements, enabling the Security Operations Center (SOC) to proactively identify and mitigate cybersecurity incidents.

The project will culminate in a heat map visually representing the sources of incoming attacks, showcasing the insights gained from both the honeynet and the SIEM system.

### Key Technologies
- **Microsoft Azure**: Virtual Network, NSG, VMs
- **Log Analytics Workspace**: KQL for data analysis
- **Microsoft Sentinel**: SIEM and incident management
- **Azure Key Vault & Storage Account**: Secure storage
- **NIST Compliance**: 800-61 Incident Handling and 800-53 Controls

## Architecture

### Before Hardening
![Architecture Before Hardening](https://i.imgur.com/aBDwnKb.jpg)

### After Hardening
![Architecture After Hardening](https://i.imgur.com/YQNa9Pp.jpg)

### Architecture Components
- **Azure Virtual Network (VNet)**
- **Network Security Groups (NSG)**
- **Virtual Machines (2 Windows, 1 Linux)**
- **Log Analytics Workspace**
- **Microsoft Sentinel**
- **Azure Key Vault & Storage Account**
- **Private Endpoints for security**

## NIST Incident Response Process

1. **Preparation**: Set up honeynet and logging capabilities.
2. **Detection and Analysis**: Monitor using Microsoft Sentinel, triggering alerts for malicious activity.
3. **Containment, Eradication, and Recovery**: Restrict traffic and eliminate threats.
4. **Post-Incident Activity**: Analyze results and improve security posture.

## Metrics

### Before Hardening (24-Hour Window)
Start Time: September 17, 2024, 10:39:37 PM (UTC) 

Stop Time: September 18, 2024, 10:39:37 PM (UTC)
| Metric                   | Count   |
| ------------------------ | ------- |
| SecurityEvent (Windows)  | 38,336  |
| Syslog (Linux)           | 2,021   |
| SecurityAlert            | 18      |
| SecurityIncident         | 177     |
| AzureNetworkAnalytics_CL  | 2,106   |

### After Hardening (24-Hour Window)
Start Time: September 21, 2024, 7:45:12 AM (UTC)

Stop Time: September 22, 2024, 7:45:12 AM (UTC)
| Metric                   | Count   |
| ------------------------ | ------- |
| SecurityEvent (Windows)  | 8,641   |
| Syslog (Linux)           | 1       |
| SecurityAlert            | 0       |
| SecurityIncident         | 0       |
| AzureNetworkAnalytics_CL  | 0       |

### Attack Maps
#### Before Hardening
-<img width="724" alt="windows-rdp-auth-fail" src="https://github.com/user-attachments/assets/a1d63861-9cf0-4f6e-8f87-208d70a3ccda">
-<img width="729" alt="linux-ssh-auth-fail" src="https://github.com/user-attachments/assets/45aaa919-74ec-49ed-962b-ab368adec92e">
-<img width="528" alt="mssql" src="https://github.com/user-attachments/assets/821cd14d-f3b1-43a2-b34f-6a16e5caa192">
-<img width="736" alt="nsg-malicious-allowed-in" src="https://github.com/user-attachments/assets/9d7fe540-cfa7-40a0-b4a9-37ca4477d3de">

#### After Hardening
```All map queries returned no results due to no instances of malicious activity for 24 hours.```

## Conclusion

The impact of the security enhancements implemented in this project is evident through substantial improvements in key metrics, aligning with NIST 800-61 and NIST 800-53 controls. Notable results include a 77.46% reduction in Windows security events, a 99.95% decrease in Linux syslog messages, and the complete elimination of security alerts and incidents after the hardening measures. Additionally, there was a 100% reduction in NSG inbound malicious flows, highlighting the effectiveness of the proactive security approach taken.

A mini honeynet was constructed in Microsoft Azure, and various log sources were integrated into a Log Analytics workspace. Microsoft Sentinel was utilized to trigger alerts and create incidents based on the ingested logs. Evaluations of metrics before and after the implementation of security controls revealed significant reductions in both security events and incidents, demonstrating the effectiveness of these measures.

It is important to recognize that if network resources were heavily utilized by regular users, there could have been an increase in security events and alerts in the 24 hours following the implementation. Overall, these outcomes affirm the success of the security enhancements, contributing to a more resilient and fortified digital environment while ensuring compliance with industry standards.

---
