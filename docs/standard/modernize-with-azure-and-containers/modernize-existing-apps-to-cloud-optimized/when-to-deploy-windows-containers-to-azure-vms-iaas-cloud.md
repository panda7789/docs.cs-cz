---
title: Když k nasazení Windows kontejnery na virtuálních počítačích Azure (IaaS cloud)
description: Modernizovat existující aplikace .NET s kontejnery cloudu Azure a Windows | Když k nasazení Windows kontejnery na virtuálních počítačích Azure (IaaS cloud)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 7472745577f414062b460fd71ab45bae85d7a62e
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a><span data-ttu-id="af485-103">Když k nasazení Windows kontejnery na virtuálních počítačích Azure (IaaS cloud)</span><span class="sxs-lookup"><span data-stu-id="af485-103">When to deploy Windows Containers to Azure VMs (IaaS cloud)</span></span>

<span data-ttu-id="af485-104">Pokud vaše organizace používá virtuálních počítačích Azure, i když používáte také Windows kontejnery, jste stále řešení IaaS.</span><span class="sxs-lookup"><span data-stu-id="af485-104">If your organization is using Azure VMs, even if you are also using Windows Containers, you are still dealing with IaaS.</span></span> <span data-ttu-id="af485-105">To znamená zabývajících se operace infrastruktury, oprav operačního systému virtuálního počítače a složitost infrastruktury pro vysoce škálovatelné aplikace, pokud budete potřebovat k nasazení na víc virtuálních počítačů na infrastruktuře vyrovnáváním zatížení.</span><span class="sxs-lookup"><span data-stu-id="af485-105">That means that dealing with infrastructure operations, VM OS patches, and infrastructure complexity for highly scalable applications when you need to deploy to multiple VMs in a load balanced infrastructure.</span></span> <span data-ttu-id="af485-106">Hlavní scénáře pro použití kontejnerů Windows virtuální počítač Azure, jsou:</span><span class="sxs-lookup"><span data-stu-id="af485-106">The main scenarios for using Windows Containers in an Azure VM are:</span></span>

-   <span data-ttu-id="af485-107">**Prostředí pro vývoj/testování**: je ideální pro vývoj a testování v cloudu A virtuálních počítačů v cloudu.</span><span class="sxs-lookup"><span data-stu-id="af485-107">**Dev/test environment**: A VM in the cloud is perfect for development and testing in the cloud.</span></span> <span data-ttu-id="af485-108">Můžete rychle vytvořit nebo zastavit prostředím podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="af485-108">You can rapidly create or stop the environment depending on your needs.</span></span>

-   <span data-ttu-id="af485-109">**Malé a střední škálovatelnost musí**: ve scénářích, kde je může být nutné si během několika virtuálních počítačů pro produkční prostředí, Správa malý počet virtuálních počítačů může být cenově dostupný dokud můžete přesunout k pokročilejším prostředí PaaS, třeba orchestrators.</span><span class="sxs-lookup"><span data-stu-id="af485-109">**Small and medium scalability needs**: In scenarios where you might need just a couple of VMs for your production environment, managing a small number of VMs might be affordable until you can move to more advanced PaaS environments, like orchestrators.</span></span>

-   <span data-ttu-id="af485-110">**Produkčním prostředí se stávajícími nástroji nasazení**: vám může přechod z prostředí na místě, ve kterém můžete investovaly do nástroje pro vytváření komplexních nasazení virtuálních počítačů nebo úplné obnovení serverů (například Puppet nebo podobné nástroje).</span><span class="sxs-lookup"><span data-stu-id="af485-110">**Production environment with existing deployment tools**: You might be moving from an on-premises environment in which you have invested in tools to make complex deployments to VMs or bare-metal servers (like Puppet or similar tools).</span></span> <span data-ttu-id="af485-111">Chcete-li přesunout do cloudu s minimálními změnami postupy nasazení produkčního prostředí, může pokračovat pomocí těchto nástrojů pro nasazení na virtuálních počítačích Azure.</span><span class="sxs-lookup"><span data-stu-id="af485-111">To move to the cloud with minimal changes to production environment deployment procedures, you might continue to use those tools to deploy to Azure VMs.</span></span> <span data-ttu-id="af485-112">Ale budete chtít použít Windows kontejnery jako jednotky nasazení lepší nasazení.</span><span class="sxs-lookup"><span data-stu-id="af485-112">However, you'll want to use Windows Containers as the unit of deployment to improve the deployment experience.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="af485-113">[Předchozí](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[další](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span><span class="sxs-lookup"><span data-stu-id="af485-113">[Previous](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Next](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span></span>
