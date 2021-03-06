---
# required metadata

title: Understand and use Lateral Movement Paths with Azure ATP | Microsoft Docs
description: This article describes the potential Lateral Movement Paths (LMPs) of Azure Advanced Threat Protection (ATP).
keywords:
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 03/31/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: de15c920-8904-4124-8bdc-03abd9f667cf

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: itargoet
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Azure ATP Lateral Movement Paths (LMPs) 

Lateral movement is when an attacker uses non-sensitive accounts to gain access to sensitive accounts throughout your network. Lateral movement is used by attackers to identify and gain access to the sensitive accounts and machines in your network that share stored log-in credentials in accounts, groups and machines. Once an attacker makes successful lateral moves towards your key targets, the attacker can also take advantage and gain access to your domain controllers. Lateral movement attacks are carried out using many of the methods described in the [Suspicious activity guide](suspicious-activity-guide.md).

A key component of Azure ATP’s security insights are Lateral Movement Paths or LMPs. Azure ATP LMPs are visual guides that help you quickly understand and identify exactly how attackers can move laterally inside your network. The purpose of lateral movements within the cyber-attack kill chain are for attackers to gain and compromise your sensitive accounts using non-sensitive accounts. Compromising your sensitive accounts gets them another step closer to their ultimate goal, domain dominance. To stop these attacks from being successful, Azure ATP LMPs give you easy to interpret, direct visual guidance on your most vulnerable, sensitive accounts. LMPs assist in helping you mitigate and prevent those risks in future, and close attacker access before they achieve domain dominance.

![Azure ATP Lateral Movement Path (LMP)](./media/atp-lmp.png)

Lateral movement attacks are typically accomplished using a number of different techniques. Some of the most popular methods used by attackers are credential theft and Pass the Ticket. In both methods, your non-sensitive accounts are used by attackers for lateral moves by exploiting non-sensitive machines that share stored log-in credentials in accounts, groups and machines with sensitive accounts.

## Where can I find Azure ATP LMPs?

Every computer or user profile discovered by Azure ATP to be in an LMP has  a **Lateral movement paths** tab. Computers and profiles with no tab have never been discovered within a potential LMP. 

![Azure ATP Lateral Movement Path (LMP) tab](./media/lateral-movement-path-tab.png)

The LMP for each entity provides different information depending on the sensitivity of the entity: 
- Sensitive users – potential LMP(s) leading to this user are shown.
- Non-sensitive users and computers – potential LMP(s) the entity is related to are shown. <br>

Each time the tab is clicked, Azure ATP displays the most recently discovered LMP. Each potential LMP is saved for 48 hours following discovery. LMP history is available. View older LMPs that were discovered in the past by clicking on **View a different date**. 

![Azure ATP Lateral Movement Path (LMP) display](./media/atp-lmp-complete.png)

Discover when potential LMPs were identified and which related entities are potentially involved. 

## LMP discovery

From the Activities tab, an indication is given when a new potential LMP was identified:
- Sensitive users – when a new path is identified to a sensitive user

![Azure ATP Lateral Movement Path (LMP) sensitive identified](./media/atp-lmp-activities.png)

- Non-sensitive users and computers – when this entity is identified in a potential LMP leading to a sensitive user.

![Azure ATP Lateral Movement Path (LMP) non-sensitive identified](./media/atp-lateral-non-sensitive.png)

## LMP related entities
LMP can now directly assists with your investigation process. Azure ATP security alert evidence lists provide the related entities that are involved in each potential lateral movement path. The evidence lists directly help your security response team increase or reduce the importance of the security alert and/or investigation of the related entities. For example, when a Pass the Ticket alert is issued, the source computer, compromised user and destination computer the stolen ticket was used from, are all part of the potential lateral movement path leading to a sensitive user. The existence of the detected LMP makes investigating the alert and watching the suspected user even more important to prevent your adversary from additional lateral moves. Trackable evidence is provided in LMPs to make it easier and faster for you to prevent attackers from moving forward in your network. 

## Lateral Movement paths to sensitive accounts report 
LMP data is also available in the [Lateral Movement Paths to Sensitive Accounts report](investigate-lateral-movement-path.md). This report lists the sensitive accounts that are exposed via lateral movement paths and includes paths that were selected manually for a specific time period, or included in the time period for scheduled reports.  Customize the included date range using the calendar selection. 

## Preventative best practices
Security insights are never too late to prevent the next attack and remediate damage. For this reason, investigating an attack even during the domain dominance phase provides a different, but important example. Typically, while investigating a security alert such as Remote Code Execution, if the alert is a true positive, your domain controller may already be compromised. But LMPs inform on where the attacker gained privileges, and what path they used into your network. Used this way, LMPs can also offer key insights into how to remediate.  

- The best way to prevent lateral movement exposure within your organization is to make sure that sensitive users only use their administrator credentials when logging into hardened computers. In the example, check if admin in the path actually needs access to the shared computer. If they do need access, make sure log in to the shared computer with a username and password other than their admin credentials.

- Verify that your users do not have unnecessary administrative permissions. In the example, check if everyone in the shared group actually requires admin rights on the exposed computer.

- Make sure people only have access to necessary resources. In the example, Ron Harper significantly widens Nick Cowley's exposure. Is it necessary that Ron Harper be included in the group? Are there subgroups that could be created to minimize lateral movement exposure?

**Tip** – When no potential lateral movement path activity is detected for an entity in the past 48 hours, choose to **View a different date** and check for previous potential lateral movement paths. The **LMP to sensitive users report** is always available is LMPs were discovered and provides you with information about potential lateral movement paths detected to sensitive users. 

**Tip** - For instructions on how to set your clients and servers to allow Azure ATP to perform the SAM-R operations needed for lateral movement path detection, see [configure SAM-R](install-atp-step8-samr.md).


## Investigating LMPs
For instructions on how to identify and investigate using Azure ATP Lateral Movement Paths, see [Investigate Lateral Movement Paths](investigate-lateral-movement-path.md).


## See Also
- [Investigating Azure ATP LMPs](investigate-lateral-movement-path.md)
- [Configure Azure ATP to make remote calls to SAM](install-atp-step8-samr.md)
- [Working with security alerts](working-with-suspicious-activities.md)
- [Check out the Azure ATP forum!](https://aka.ms/azureatpcommunity)
