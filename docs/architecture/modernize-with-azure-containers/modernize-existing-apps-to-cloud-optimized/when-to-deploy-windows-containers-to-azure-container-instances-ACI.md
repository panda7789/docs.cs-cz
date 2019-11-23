---
title: Kdy nasadit kontejnery Windows do Azure Container Instances (ACI)
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Kdy nasadit kontejnery Windows do Azure Container Instances (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2019
ms.locfileid: "68676907"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="29c6d-103">Kdy nasadit kontejnery Windows do Azure Container Instances (ACI)</span><span class="sxs-lookup"><span data-stu-id="29c6d-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="29c6d-104">Azure Container Instances hlavní pozice hodnoty znamená, že můžete k němu nasazovat kontejnery a nemusíte ho udržovat, nemusíte upgradovat/opravovat základní operační systémy nebo virtuální počítače, které jsou transparentní a Vy jenom nasadíte kontejnery do prostředí připravené k použití.</span><span class="sxs-lookup"><span data-stu-id="29c6d-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="29c6d-105">Důvody a scénáře, kdy byste chtěli použít ACI, jsou podobné hlavním scénářům při použití virtuálních počítačů Azure s kontejnery, a to v podstatě hlavní scénáře použití Azure Container Instances:</span><span class="sxs-lookup"><span data-stu-id="29c6d-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="29c6d-106">**Scénáře pro vývoj a testování**</span><span class="sxs-lookup"><span data-stu-id="29c6d-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="29c6d-107">**Automatizace úloh**</span><span class="sxs-lookup"><span data-stu-id="29c6d-107">**Task automation**</span></span>
- <span data-ttu-id="29c6d-108">**Agenti CI/CD**</span><span class="sxs-lookup"><span data-stu-id="29c6d-108">**CI/CD agents**</span></span>
- <span data-ttu-id="29c6d-109">**Dávkové zpracování malých nebo škálovatelných**</span><span class="sxs-lookup"><span data-stu-id="29c6d-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="29c6d-110">**Jednoduché webové aplikace**</span><span class="sxs-lookup"><span data-stu-id="29c6d-110">**Simple web apps**</span></span>

<span data-ttu-id="29c6d-111">Scénář jednoduché webové aplikace je spravedlivý scénář pro ACI, ale vezme v úvahu, že protože v ACI máte jenom jednu instanci kontejneru na Image kontejneru, nebudete mít vysokou dostupnost a máte jenom omezené škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="29c6d-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="29c6d-112">I když se ACI považuje za infrastrukturu, protože poskytuje jenom jednu instanci kontejneru, je ve srovnání s běžnými virtuálními počítači Azure s Windows serverem velký přínos.</span><span class="sxs-lookup"><span data-stu-id="29c6d-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="29c6d-113">V ACI stačí nasadit kontejnery do samostatného prostředí a Vy jenom platíte za tyto kontejnery.</span><span class="sxs-lookup"><span data-stu-id="29c6d-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="29c6d-114">Nemusíte spravovat/aktualizovat/opravovat virtuální počítače, takže je to mnohem lepší platforma pro většinu scénářů, ve kterých můžete používat virtuální počítače s kontejnery.</span><span class="sxs-lookup"><span data-stu-id="29c6d-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="29c6d-115">Použití ACI je rovné, stačí pouze nasadit kontejner, takže nemusíte vytvářet prostředí virtuálních počítačů, které pouze nasazujete kontejnery.</span><span class="sxs-lookup"><span data-stu-id="29c6d-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="29c6d-116">Hlavní výhody Azure Container Instances (ACI) jsou:</span><span class="sxs-lookup"><span data-stu-id="29c6d-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="29c6d-117">Spouštění kontejnerů bez správy serverů</span><span class="sxs-lookup"><span data-stu-id="29c6d-117">Run containers without managing servers</span></span>
- <span data-ttu-id="29c6d-118">Zvýšení flexibility pomocí kontejnerů na vyžádání</span><span class="sxs-lookup"><span data-stu-id="29c6d-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="29c6d-119">Pomocí jediného příkazu můžete nasadit kontejnery do cloudu s nepředchůdci a rychlostí.</span><span class="sxs-lookup"><span data-stu-id="29c6d-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="29c6d-120">Zabezpečení aplikací s izolací hypervisoru</span><span class="sxs-lookup"><span data-stu-id="29c6d-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="29c6d-121">V krátkém ACI můžete rychle vyvíjet aplikace bez nutnosti spravovat virtuální počítače nebo se seznámit s novými nástroji.</span><span class="sxs-lookup"><span data-stu-id="29c6d-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="29c6d-122">Je to jenom vaše aplikace v kontejneru spuštěná v cloudu.</span><span class="sxs-lookup"><span data-stu-id="29c6d-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="29c6d-123">[Předchozí](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [Další](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="29c6d-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
