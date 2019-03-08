---
title: Kdy nasadit kontejnery Windows do Azure Container Instances (ACI)
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Kdy nasadit kontejnery Windows do Azure Container Instances (ACI)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 03ee7c8b65e1a92dcc7fd40b44e9ba081f571487
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674403"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="7ba37-103">Kdy nasadit kontejnery Windows do Azure Container Instances (ACI)</span><span class="sxs-lookup"><span data-stu-id="7ba37-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="7ba37-104">Služba Azure Container Instances, hlavní hodnotové je, můžete okamžitě nasazení kontejnerů do ní a není nutné udržovat prostředí, není nutné upgradování, opravování základní operační systém nebo virtuálních počítačů, všechny, které je transparentní a jen nasadit kontejnery do prostředí připravené k použití.</span><span class="sxs-lookup"><span data-stu-id="7ba37-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="7ba37-105">Z důvodů a scénáře, kdy je vhodné použít ACI jsou podobné hlavní scénáře, pokud používáte virtuální počítače Azure s kontejnery, tedy v podstatě, jsou hlavní scénáře pomocí služby Azure Container Instances:</span><span class="sxs-lookup"><span data-stu-id="7ba37-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="7ba37-106">**Scénáře vývoje/testování**</span><span class="sxs-lookup"><span data-stu-id="7ba37-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="7ba37-107">**Automatizace úloh**</span><span class="sxs-lookup"><span data-stu-id="7ba37-107">**Task automation**</span></span>
- <span data-ttu-id="7ba37-108">**Agenti CI/CD**</span><span class="sxs-lookup"><span data-stu-id="7ba37-108">**CI/CD agents**</span></span>
- <span data-ttu-id="7ba37-109">**Dávkové zpracování (krátkodobé používání) nebo exponent**</span><span class="sxs-lookup"><span data-stu-id="7ba37-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="7ba37-110">**Jednoduché webové aplikace**</span><span class="sxs-lookup"><span data-stu-id="7ba37-110">**Simple web apps**</span></span>

<span data-ttu-id="7ba37-111">Scénář jednoduché webové aplikace je veletrh scénářem ACI, ale vezměte v úvahu, že vzhledem k tomu, že v ACI může mít pouze jeden kontejner instance za image kontejneru, nebudou mít vysokou dostupnost a pouze omezená škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="7ba37-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="7ba37-112">Nicméně i v případě, že ACI je považován za infrastrukturu, protože poskytuje právě jeden kontejner instancí, je obrovská výhoda ve srovnání s běžnými virtuálními počítači Azure s Windows serverem.</span><span class="sxs-lookup"><span data-stu-id="7ba37-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="7ba37-113">Pomocí ACI jen nasadit kontejnery do prostředí s místním udržované a platíte jenom za těchto kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="7ba37-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="7ba37-114">Není nutné udržovat/aktualizací a oprav virtuálních počítačů, tak, aby byl mnohem lepší platformu pro většinu scénářů, kde je možné, že používáte virtuální počítače s kontejnery.</span><span class="sxs-lookup"><span data-stu-id="7ba37-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="7ba37-115">Pomocí ACI je snadná, stačí nasadit kontejner, není nutné k vytvoření virtuálního počítače prostředí jen nasadit kontejnery.</span><span class="sxs-lookup"><span data-stu-id="7ba37-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="7ba37-116">Hlavní výhody služby Azure Container Instances (ACI) jsou:</span><span class="sxs-lookup"><span data-stu-id="7ba37-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="7ba37-117">Spouštění kontejnerů bez správy serverů</span><span class="sxs-lookup"><span data-stu-id="7ba37-117">Run containers without managing servers</span></span>
- <span data-ttu-id="7ba37-118">Zvýšení agility s kontejnery na vyžádání</span><span class="sxs-lookup"><span data-stu-id="7ba37-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="7ba37-119">Nasazení kontejnerů do cloudu mimořádně rychle a snadno – pomocí jediného příkazu.</span><span class="sxs-lookup"><span data-stu-id="7ba37-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="7ba37-120">Zabezpečené aplikace s izolací hypervisoru</span><span class="sxs-lookup"><span data-stu-id="7ba37-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="7ba37-121">Stručně řečeno s ACI můžete vyvíjet aplikace rychle bez správu virtuálních počítačů a nemusíte se učit nové nástroje.</span><span class="sxs-lookup"><span data-stu-id="7ba37-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="7ba37-122">Je to jenom vaše aplikace v kontejneru spuštěná v cloudu.</span><span class="sxs-lookup"><span data-stu-id="7ba37-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="7ba37-123">[Předchozí](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [další](when-to-deploy-windows-containers-to-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="7ba37-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-service-fabric.md)</span></span>
