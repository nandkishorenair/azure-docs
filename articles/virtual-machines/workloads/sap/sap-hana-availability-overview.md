---
title: SAP HANA Availability on Azure VMs - Overview | Microsoft Docs
description: Operations of SAP HANA on Azure native VMs
services: virtual-machines-linux,virtual-machines-windows
documentationcenter: ''
author: msjuergent
manager: patfilot
editor: ''
tags: azure-resource-manager
keywords: ''

ms.service: virtual-machines-linux
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: vm-linux
ms.workload: infrastructure
ms.date: 02/26/2018
ms.author: juergent
ms.custom: H1Hack27Feb2017

---

# SAP HANA High Availability guide for Azure virtual machines
Azure provides numerous capabilities that allows to deploy mission critical databases like SAP HANA in Azure VMs. This document provides guidance on how to achieve availability for SAP HANA instances that are hosted in Azure Virtual Machines. Within the document, several scenarios that can be implemented on Azure infrastructure to increase availability of SAP HANA on Azure are described. 

## Prerequisites
This guide assumes that you are familiar with such Infrastructure as a service (IaaS) basics on Azure as: 

- How to deploy virtual machines or virtual networks via the Azure portal or PowerShell.
- The Azure cross-platform command-line interface (CLI), including the option to use JavaScript Object Notation (JSON) templates.

This guide also assumes that you are familiar with installing SAP HANA instances and administrating and operating SAP HANA instances. Especially set up and operations around HANA System Replication or tasks like backup and restore of SAP HANA databases.

Other articles that give a good overview on SAP HANA topics in Azure are:

- [Manual installation of single-instance SAP HANA on Azure VMs](https://docs.microsoft.com/azure/virtual-machines/workloads/sap/hana-get-started)
- [Setup SAP HANA System Replication in Azure VMs](sap-hana-high-availability.md)
- [Backup guide for SAP HANA on Azure Virtual Machines](https://docs.microsoft.com/azure/virtual-machines/workloads/sap/sap-hana-backup-guide)

Article and content you should be familiar about SAP HANA can be listed like:

- [High Availability for SAP HANA](https://help.sap.com/viewer/6b94445c94ae495c83a19646e7c3fd56/2.0.02/en-US/6d252db7cdd044d19ad85b46e6c294a4.html)
- [FAQ: High Availability for SAP HANA](https://archive.sap.com/documents/docs/DOC-66702)
- [How to Perform System Replication for SAP HANA](https://archive.sap.com/documents/docs/DOC-47702)
- [SAP HANA 2.0 SPS 01 What’s New: High Availability](https://blogs.sap.com/2017/05/15/sap-hana-2.0-sps-01-whats-new-high-availability-by-the-sap-hana-academy/)
- [Network Recommendations for SAP HANA System Replication](https://www.sap.com/documents/2016/06/18079a1c-767c-0010-82c7-eda71af511fa.html)
- [SAP HANA System Replication](https://help.sap.com/viewer/6b94445c94ae495c83a19646e7c3fd56/2.0.01/en-US/b74e16a9e09541749a745f41246a065e.html)
- [SAP HANA Service Auto-Restart](https://help.sap.com/viewer/6b94445c94ae495c83a19646e7c3fd56/2.0.01/en-US/cf10efba8bea4e81b1dc1907ecc652d3.html)
- [Configuring SAP HANA System Replication](https://help.sap.com/viewer/6b94445c94ae495c83a19646e7c3fd56/2.0.01/en-US/676844172c2442f0bf6c8b080db05ae7.html)


Beyond being familiar with deploying VMs in Azure, we also recommend reading the article [Manage the availability of Windows virtual machines in Azure](https://docs.microsoft.com/azure/virtual-machines/windows/manage-availability) first before continuing with defining your availability architecture in Azure.

## Service Level agreements for different Azure components
Azure has different availability SLAs for different components like networking, storage, and VMs. All these SLAs are documented and can be found starting with the [Microsoft Azure Service Level Agreement](https://azure.microsoft.com/support/legal/sla/) page. If you check out the [SLA for Virtual Machines](https://azure.microsoft.com/support/legal/sla/virtual-machines/v1_6/), you realize that Azure provides two different SLAs with two different configurations. The SLAs are defined like:

- A single VM using [Azure Premium Storage](https://docs.microsoft.com/azure/virtual-machines/windows/premium-storage) for the OS disk and all data disks provides a monthly up-time percentage of 99.9%
- Multiple (at least two) VMs that are organized in an [Azure Availability Set](https://docs.microsoft.com/azure/virtual-machines/windows/tutorial-availability-sets) provide a monthly up-time percentage of 99.95%

Measure your requirement of availability against the SLAs Azure components can provide and then decide on the different scenarios you need to implement with SAP HANA to achieve the availability you require to provide.















  


