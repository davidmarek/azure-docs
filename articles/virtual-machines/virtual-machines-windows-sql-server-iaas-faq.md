---
title: SQL Server on Azure Virtual Machines FAQ | Microsoft Docs
description: This article provides answers to frequently asked questions about running SQL Server on Azure VMs.
services: virtual-machines-windows
documentationcenter: ''
author: v-shysun
manager: felixwu
editor: ''
tags: azure-service-management

ms.assetid: 2fa5ee6b-51a6-4237-805f-518e6c57d11b
ms.service: virtual-machines-sql
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: vm-windows-sql-server
ms.workload: iaas-sql-server
ms.date: 11/30/2016
ms.author: v-shysun

---
# SQL Server on Azure Virtual Machines FAQ
This topic provides answers to some of the most common questions about running [SQL Server on Azure Virtual Machines](https://azure.microsoft.com/services/virtual-machines/sql-server/).

[!INCLUDE [support-disclaimer](../../includes/support-disclaimer.md)]

## Frequently Asked Questions
1. **How do I create an Azure virtual machine with SQL Server?**
   
    The easiest solution is to create a Virtual Machine that includes SQL Server. For a tutorial on signing up for Azure and creating a SQL VM from the portal, see [Provision a SQL Server virtual machine in the Azure Portal](virtual-machines-windows-portal-sql-server-provision.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json). You can select a virtual machine image that uses pay-per-minute SQL Server licensing, or you can use an image that allows you to bring your own SQL Server license. You also have the option of manually installing SQL Server on a VM and reusing an on-premises license. If you bring your own license, you must have [License Mobility through Software Assurance on Azure](https://azure.microsoft.com/pricing/license-mobility/).
2. **What is the difference between SQL VMs and the SQL Database service?**
   
    Conceptually, running SQL Server on an Azure virtual machine is not that different from running SQL Server in a remote datacenter. In contrast, [SQL Database](../sql-database/sql-database-technical-overview.md) offers database-as-a-service. With SQL Database, you do not have access to the machines that host your databases. For a full comparison, see [Choose a cloud SQL Server option: Azure SQL (PaaS) Database or SQL Server on Azure VMs (IaaS)](../sql-database/sql-database-paas-vs-sql-server-iaas.md).
3. **How can I migrate my on-premises SQL Server database to the Cloud?**
   
    First create an Azure virtual machine with a SQL Server instance. Then migrate your on-premises databases to that instance. For data migration strategies, see [Migrate a SQL Server database to SQL Server in an Azure VM](virtual-machines-windows-migrate-sql.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json).
4. **Can I change the installed features or install a second instance of SQL Server on the same VM?**
   
    Yes. The SQL Server installation media is located in a folder on the **C** drive. Run **Setup.exe** from that location to add new SQL Server instances or to change other installed features of SQL Server on the machine.
5. **How do I upgrade to a new version/edition of the SQL Server in an Azure VM?**
   
    Currently, there is no in-place upgrade for SQL Server running in an Azure VM. Create a new Azure virtual machine with the desired SQL Server version/edition, and then migrate your databases to the new server using standard [data migration techniques](virtual-machines-windows-migrate-sql.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json).
6. **How can I install my licensed copy of SQL Server on an Azure VM?**
   
    There are two ways to do this. You can provision one of the [virtual machine images that supports licenses](virtual-machines-windows-sql-server-iaas-overview.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#BYOL). Another option is to copy the SQL Server installation media to a Windows Server VM, and then install SQL Server on the VM. For licensing reasons, you must have [License Mobility through Software Assurance on Azure](https://azure.microsoft.com/pricing/license-mobility/).
7. **Can I change a VM to use my own SQL Server license if it was created from one of the pay-as-you-go gallery images?**

    No. You can not switch from pay-per-minute licensing to using your own license. Create a new Azure virtual machine using one of the [BYOL images](virtual-machines-windows-sql-server-iaas-overview.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#BYOL), and then migrate your databases to the new server using standard [data migration techniques](virtual-machines-windows-migrate-sql.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json).
7. **Do you have to pay the SQL costs of a VM if it is only being used for standby/failover?**
   
    If you are creating the SQL VM through the gallery, then you must have a separate license for the standby SQL VM and the pricing is the same. If you install SQL Server manually on a virtual machine with [License Mobility](https://azure.microsoft.com/pricing/license-mobility/), you have the option to have one free passive SQL instance for failover. Please review the restrictions and requirements.
8. **How are updates and service packs applied on a SQL Server VM?**
   
    Virtual machines give you control over the host machine, including when and how you apply updates. For the operating system, you can manually apply windows updates, or you can enable a scheduling service called [Automated Patching](virtual-machines-windows-classic-sql-automated-patching.md?toc=%2fazure%2fvirtual-machines%2fwindows%2fclassic%2ftoc.json). Automated Patching installs any updates that are marked important, including SQL Server updates in that category. Other optional updates to SQL Server must be installed manually.
9. **Is it possible to set up configurations not shown in the virtual machine gallery (For example Windows 2008 R2 + SQL Server 2012)?**
   
    No. For virtual machine gallery images that include SQL Server, you must select one of the provided images.
10. **How do I install SQL Data tools on my Azure VM?**
    
     Download and install the SQL Data tools from [Microsoft SQL Server Data Tools - Business Intelligence for Visual Studio 2013 ](https://www.microsoft.com/en-us/download/details.aspx?id=42313).

## Resources
For an overview of SQL Server on Azure Virtual Machines, watch the video [Azure VM is the best platform for SQL Server 2016](https://channel9.msdn.com/Events/DataDriven/SQLServer2016/Azure-VM-is-the-best-platform-for-SQL-Server-2016). You can also get a good introduction in the topic, [SQL Server on Azure Virtual Machines overview](virtual-machines-windows-sql-server-iaas-overview.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json).

Other resources include:

* [Provision a SQL Server virtual machine in the Azure Portal](virtual-machines-windows-portal-sql-server-provision.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json)
* [Migrating a Database to SQL Server on an Azure VM](virtual-machines-windows-migrate-sql.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json)
* [High Availability and Disaster Recovery for SQL Server in Azure Virtual Machines](virtual-machines-windows-sql-high-availability-dr.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json)
* [Performance best practices for SQL Server in Azure Virtual Machines](virtual-machines-windows-sql-performance.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json)
* [Application Patterns and Development Strategies for SQL Server in Azure Virtual Machines](virtual-machines-windows-sql-server-app-patterns-dev-strategies.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json)

