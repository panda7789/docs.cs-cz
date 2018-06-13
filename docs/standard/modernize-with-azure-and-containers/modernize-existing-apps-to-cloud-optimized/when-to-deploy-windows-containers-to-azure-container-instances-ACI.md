---
title: Při nasazení kontejnerů Windows do Azure kontejner instancí (ACI)
description: Modernizovat existující aplikace .NET s kontejnery cloudu Azure a Windows | Při nasazení kontejnerů Windows do Azure kontejner instancí (ACI)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 3dc23c96543d9611763b571105f52b150dfec06f
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958224"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="a0e70-103">Při nasazení kontejnerů Windows do Azure kontejner instancí (ACI)</span><span class="sxs-lookup"><span data-stu-id="a0e70-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="a0e70-104">Azure instancí kontejnerů, které hlavní hodnotu je, že k němu můžete hned nasadit kontejnery a nemusíte spravovat prostředí, není třeba upgrade nebo opravu podkladové operační systém nebo virtuálních počítačů, všechny které je transparentní a jen nasadit kontejnery do prostředí připravené k použití.</span><span class="sxs-lookup"><span data-stu-id="a0e70-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlaying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="a0e70-105">Scénáře, kdy je vhodné použít ACI a z důvodů je podobná hlavní scénáře, když používáte virtuální počítače Azure s kontejnery, proto je v podstatě, hlavní scénáře pomocí Azure kontejner instancí jsou:</span><span class="sxs-lookup"><span data-stu-id="a0e70-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

-   <span data-ttu-id="a0e70-106">**Scénáře vývoje/testování**</span><span class="sxs-lookup"><span data-stu-id="a0e70-106">**Dev/Test scenarios**</span></span>
-   <span data-ttu-id="a0e70-107">**Automatizace úloh**</span><span class="sxs-lookup"><span data-stu-id="a0e70-107">**Task automation**</span></span>
-   <span data-ttu-id="a0e70-108">**Agenti CI/CD**</span><span class="sxs-lookup"><span data-stu-id="a0e70-108">**CI/CD agents**</span></span>
-   <span data-ttu-id="a0e70-109">**Malá nebo škálování dávkové zpracování**</span><span class="sxs-lookup"><span data-stu-id="a0e70-109">**Small/scale batch processing**</span></span>
-   <span data-ttu-id="a0e70-110">**Jednoduché webové aplikace**</span><span class="sxs-lookup"><span data-stu-id="a0e70-110">**Simple web apps**</span></span>

<span data-ttu-id="a0e70-111">Tento scénář jednoduché webové aplikace je správného scénáře pro ACI ale vezměte v úvahu, že vzhledem k tomu, že v ACI může mít pouze instance jediný kontejner pro bitovou kopii kontejneru, nebude mít vysokou dostupnost a mají omezenou škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="a0e70-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="a0e70-112">I když ACI se považuje za infrastrukturu, protože nabízí jen jediný kontejner instancí, je však obrovské výhody ve srovnání s regulární virtuálních počítačích Azure se systémem Windows Server.</span><span class="sxs-lookup"><span data-stu-id="a0e70-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="a0e70-113">S ACI jen nasadit kontejnery do prostředí samoobslužné zachována a platíte jenom za těchto kontejnerech.</span><span class="sxs-lookup"><span data-stu-id="a0e70-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="a0e70-114">Nemusíte spravovat/aktualizace nebo opravy virtuálních počítačů, takže je mnohem lepší platformu pro většinu scénářů, kde můžete používat virtuální počítače s kontejnery.</span><span class="sxs-lookup"><span data-stu-id="a0e70-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="a0e70-115">Použití ACI je přímo dál, jen nasadit kontejner, není nutné k vytvoření prostředí virtuálních počítačů právě nasazení kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="a0e70-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="a0e70-116">Hlavní výhody z Azure kontejner instancí (ACI) jsou:</span><span class="sxs-lookup"><span data-stu-id="a0e70-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

-   <span data-ttu-id="a0e70-117">Spustit kontejnery bez Správa serverů</span><span class="sxs-lookup"><span data-stu-id="a0e70-117">Run containers without managing servers</span></span>
-   <span data-ttu-id="a0e70-118">Zvýšení flexibility s kontejnery na vyžádání</span><span class="sxs-lookup"><span data-stu-id="a0e70-118">Increase agility with containers on demand</span></span>
-   <span data-ttu-id="a0e70-119">Kontejnery můžete nasadit do cloudu s nebývalá jednoduchost a rychlost – jedním příkazem.</span><span class="sxs-lookup"><span data-stu-id="a0e70-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span> 
-   <span data-ttu-id="a0e70-120">Zabezpečené aplikace s izolací hypervisoru</span><span class="sxs-lookup"><span data-stu-id="a0e70-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="a0e70-121">Stručně řečeno s ACI můžete vyvíjet aplikace, rychlé bez správu virtuálních počítačů, nebo máte nové nástroje.</span><span class="sxs-lookup"><span data-stu-id="a0e70-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="a0e70-122">Je právě aplikace v kontejneru, běží v cloudu.</span><span class="sxs-lookup"><span data-stu-id="a0e70-122">It's just your application, in a container, running in the cloud.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="a0e70-123">[Předchozí](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[další](when-to-deploy-windows-containers-to-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="a0e70-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-service-fabric.md)</span></span>
