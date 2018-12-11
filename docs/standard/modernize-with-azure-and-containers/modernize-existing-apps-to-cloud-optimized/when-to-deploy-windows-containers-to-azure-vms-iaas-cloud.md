---
title: Kdy nasadit kontejnery Windows na virtuálních počítačích Azure (IaaS cloud)
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Kdy nasadit kontejnery Windows na virtuálních počítačích Azure (IaaS cloud)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 51217e2c94fd9727c8f7907e791cdebaec98f14f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152146"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a><span data-ttu-id="1ab67-103">Kdy nasadit kontejnery Windows na virtuálních počítačích Azure (IaaS cloud)</span><span class="sxs-lookup"><span data-stu-id="1ab67-103">When to deploy Windows Containers to Azure VMs (IaaS cloud)</span></span>

<span data-ttu-id="1ab67-104">Pokud vaše organizace používá virtuální počítače Azure i v případě také použijete kontejnery Windows, budete pořád řešení IaaS.</span><span class="sxs-lookup"><span data-stu-id="1ab67-104">If your organization is using Azure VMs, even if you are also using Windows Containers, you are still dealing with IaaS.</span></span> <span data-ttu-id="1ab67-105">To znamená zabývajících se operace infrastrukturu, opravy operačního systému virtuálního počítače a složitosti infrastruktury pro vysoce škálovatelné aplikace. když budete chtít nasadit víc virtuálních počítačů v infrastruktuře s vyrovnáváním zatížení.</span><span class="sxs-lookup"><span data-stu-id="1ab67-105">That means that dealing with infrastructure operations, VM OS patches, and infrastructure complexity for highly scalable applications when you need to deploy to multiple VMs in a load balanced infrastructure.</span></span> <span data-ttu-id="1ab67-106">Hlavní scénáře pro použití kontejnerů Windows ve Virtuálním počítači Azure jsou:</span><span class="sxs-lookup"><span data-stu-id="1ab67-106">The main scenarios for using Windows Containers in an Azure VM are:</span></span>

-   <span data-ttu-id="1ab67-107">**Prostředí pro vývoj/testování**: Virtuální počítač v cloudu je ideální pro vývoj a testování v cloudu.</span><span class="sxs-lookup"><span data-stu-id="1ab67-107">**Dev/test environment**: A VM in the cloud is perfect for development and testing in the cloud.</span></span> <span data-ttu-id="1ab67-108">Můžete rychle vytvořit nebo zastavení prostředí podle svých potřeb.</span><span class="sxs-lookup"><span data-stu-id="1ab67-108">You can rapidly create or stop the environment depending on your needs.</span></span>

-   <span data-ttu-id="1ab67-109">**Malé a střední škálovatelnost potřebuje**: Ve scénářích, které vyžadují několika virtuálních počítačů pro produkční prostředí Správa malé množství virtuálních počítačů může být cenově dokud nepřejdete na pokročilejší prostředí PaaS, jako je orchestrátorů.</span><span class="sxs-lookup"><span data-stu-id="1ab67-109">**Small and medium scalability needs**: In scenarios where you might need just a couple of VMs for your production environment, managing a small number of VMs might be affordable until you can move to more advanced PaaS environments, like orchestrators.</span></span>

-   <span data-ttu-id="1ab67-110">**Produkční prostředí se stávajícími nástroji nasazení**: Vám může přesun z v místním prostředí, ve kterém jste investovali v nástroji pro zajištění komplexních nasazení do virtuálních počítačů nebo serverů na holé počítače (jako jsou Puppet nebo podobné nástroje).</span><span class="sxs-lookup"><span data-stu-id="1ab67-110">**Production environment with existing deployment tools**: You might be moving from an on-premises environment in which you have invested in tools to make complex deployments to VMs or bare-metal servers (like Puppet or similar tools).</span></span> <span data-ttu-id="1ab67-111">Pokud chcete přesunout do cloudu s minimálními změnami na postupy nasazení produkčního prostředí, může dál používat tyto nástroje k nasazení do virtuálních počítačů Azure.</span><span class="sxs-lookup"><span data-stu-id="1ab67-111">To move to the cloud with minimal changes to production environment deployment procedures, you might continue to use those tools to deploy to Azure VMs.</span></span> <span data-ttu-id="1ab67-112">Ale budete chtít používat kontejnery Windows jako jednotky nasazení vylepšit celkovou funkčnost nasazení.</span><span class="sxs-lookup"><span data-stu-id="1ab67-112">However, you'll want to use Windows Containers as the unit of deployment to improve the deployment experience.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1ab67-113">[Předchozí](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[další](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span><span class="sxs-lookup"><span data-stu-id="1ab67-113">[Previous](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Next](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span></span>