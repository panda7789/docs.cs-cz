---
title: "Když k nasazení Windows kontejnery na virtuálních počítačích Azure (IaaS cloud)"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Když k nasazení Windows kontejnery na virtuálních počítačích Azure (IaaS cloud)"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 832faed135d5b8ec9f8ad0a6ca82b5fac0273284
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a><span data-ttu-id="f7329-103">Když k nasazení Windows kontejnery na virtuálních počítačích Azure (IaaS cloud)</span><span class="sxs-lookup"><span data-stu-id="f7329-103">When to deploy Windows Containers to Azure VMs (IaaS cloud)</span></span>

<span data-ttu-id="f7329-104">Pokud vaše organizace používá virtuálních počítačích Azure, i když používáte také Windows kontejnery, jste stále řešení IaaS.</span><span class="sxs-lookup"><span data-stu-id="f7329-104">If your organization is using Azure VMs, even if you are also using Windows Containers, you are still dealing with IaaS.</span></span> <span data-ttu-id="f7329-105">To znamená zabývajících se operace infrastruktury, oprav operačního systému virtuálního počítače a složitost infrastruktury pro vysoce škálovatelné aplikace, pokud budete potřebovat k nasazení na víc virtuálních počítačů na infrastruktuře vyrovnáváním zatížení.</span><span class="sxs-lookup"><span data-stu-id="f7329-105">That means that dealing with infrastructure operations, VM OS patches, and infrastructure complexity for highly scalable applications when you need to deploy to multiple VMs in a load balanced infrastructure.</span></span> <span data-ttu-id="f7329-106">Hlavní scénáře pro použití kontejnerů Windows virtuální počítač Azure, jsou:</span><span class="sxs-lookup"><span data-stu-id="f7329-106">The main scenarios for using Windows Containers in an Azure VM are:</span></span>

-   <span data-ttu-id="f7329-107">**Prostředí pro vývoj/testování**: je ideální pro vývoj a testování v cloudu A virtuálních počítačů v cloudu.</span><span class="sxs-lookup"><span data-stu-id="f7329-107">**Dev/test environment**: A VM in the cloud is perfect for development and testing in the cloud.</span></span> <span data-ttu-id="f7329-108">Můžete rychle vytvořit nebo zastavit prostředím podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="f7329-108">You can rapidly create or stop the environment depending on your needs.</span></span>

-   <span data-ttu-id="f7329-109">**Malé a střední škálovatelnost musí**: ve scénářích, kde je může být nutné si během několika virtuálních počítačů pro produkční prostředí, Správa malý počet virtuálních počítačů může být cenově dostupný dokud můžete přesunout k pokročilejším prostředí PaaS, třeba orchestrators.</span><span class="sxs-lookup"><span data-stu-id="f7329-109">**Small and medium scalability needs**: In scenarios where you might need just a couple of VMs for your production environment, managing a small number of VMs might be affordable until you can move to more advanced PaaS environments, like orchestrators.</span></span>

-   <span data-ttu-id="f7329-110">**Produkčním prostředí se stávajícími nástroji nasazení**: vám může přechod z prostředí na místě, ve kterém můžete investovaly do nástroje pro vytváření komplexních nasazení virtuálních počítačů nebo úplné obnovení serverů (například Puppet nebo podobné nástroje).</span><span class="sxs-lookup"><span data-stu-id="f7329-110">**Production environment with existing deployment tools**: You might be moving from an on-premises environment in which you have invested in tools to make complex deployments to VMs or bare-metal servers (like Puppet or similar tools).</span></span> <span data-ttu-id="f7329-111">Chcete-li přesunout do cloudu s minimálními změnami postupy nasazení produkčního prostředí, může pokračovat pomocí těchto nástrojů pro nasazení na virtuálních počítačích Azure.</span><span class="sxs-lookup"><span data-stu-id="f7329-111">To move to the cloud with minimal changes to production environment deployment procedures, you might continue to use those tools to deploy to Azure VMs.</span></span> <span data-ttu-id="f7329-112">Ale budete chtít použít Windows kontejnery jako jednotky nasazení lepší nasazení.</span><span class="sxs-lookup"><span data-stu-id="f7329-112">However, you'll want to use Windows Containers as the unit of deployment to improve the deployment experience.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="f7329-113">[Předchozí](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[další](when-to-deploy-windows-containers-to-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="f7329-113">[Previous](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Next](when-to-deploy-windows-containers-to-service-fabric.md)</span></span>
