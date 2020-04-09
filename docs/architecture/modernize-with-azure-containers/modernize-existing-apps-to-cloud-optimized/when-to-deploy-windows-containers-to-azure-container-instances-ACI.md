---
title: Kdy nasadit kontejnery Windows do instancí kontejnerů Azure (ACI)
description: Modernizace stávajících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Kdy nasadit kontejnery Windows do instancí kontejnerů Azure (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 6c889db6f0475f24a196144c7fb62faec4c173ed
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989152"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="e1391-103">Kdy nasadit kontejnery Windows do instancí kontejnerů Azure (ACI)</span><span class="sxs-lookup"><span data-stu-id="e1391-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="e1391-104">Azure Container Instances hlavní hodnota návrh je, že můžete okamžitě nasadit kontejnery do něj a nemusíte udržovat toto prostředí, nemusíte upgradovat/opravit základní operační systém nebo virtuální počítače, vše, co je transparentní a stačí nasadit kontejnery do připraveného k použití prostředí.</span><span class="sxs-lookup"><span data-stu-id="e1391-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don't need to maintain that environment, you don't need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="e1391-105">Důvody a scénáře, když byste chtěli použít ACI jsou podobné hlavní scénáře při použití virtuálních počítačích Azure s kontejnery, takže v podstatě hlavní scénáře pro použití Azure Container Instances jsou:</span><span class="sxs-lookup"><span data-stu-id="e1391-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="e1391-106">**Scénáře pro vývoj a testování**</span><span class="sxs-lookup"><span data-stu-id="e1391-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="e1391-107">**Automatizace úloh**</span><span class="sxs-lookup"><span data-stu-id="e1391-107">**Task automation**</span></span>
- <span data-ttu-id="e1391-108">**Ci/CD agenti**</span><span class="sxs-lookup"><span data-stu-id="e1391-108">**CI/CD agents**</span></span>
- <span data-ttu-id="e1391-109">**Malé/zmenšené dávkové zpracování**</span><span class="sxs-lookup"><span data-stu-id="e1391-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="e1391-110">**Jednoduché webové aplikace**</span><span class="sxs-lookup"><span data-stu-id="e1391-110">**Simple web apps**</span></span>

<span data-ttu-id="e1391-111">Jednoduchý scénář webových aplikací je spravedlivý scénář pro ACI, ale vezměte v úvahu, že vzhledem k tomu, že v ACI můžete mít pouze jednu instanci kontejneru na bitovou kopii kontejneru, nebudete mít vysokou dostupnost a máte pouze omezenou škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="e1391-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won't have high availability and only have limited scalability.</span></span>

<span data-ttu-id="e1391-112">I v případě, že aci je považován za infrastrukturu, protože poskytuje pouze jeden kontejner instance, je obrovská výhoda ve srovnání s běžnými virtuálními počítači Azure s Windows Server.</span><span class="sxs-lookup"><span data-stu-id="e1391-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="e1391-113">S ACI, stačí nasadit kontejnery do prostředí s vlastním údržbou a stačí zaplatit za tyto kontejnery.</span><span class="sxs-lookup"><span data-stu-id="e1391-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="e1391-114">Nemusíte udržovat/ aktualizovat/opravovat virtuální uživatele, takže je to mnohem lepší platforma pro většinu scénářů, kde můžete používat virtuální aplikace s kontejnery.</span><span class="sxs-lookup"><span data-stu-id="e1391-114">You don't need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="e1391-115">Použití ACI je přímočaré, stačí nasadit kontejner, není třeba vytvářet prostředí virtuálního uživatele, které právě nasadíte kontejnery.</span><span class="sxs-lookup"><span data-stu-id="e1391-115">Using ACI is straight forward, you just deploy a container, there's no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="e1391-116">Hlavní výhody azure container instance (ACI) jsou:</span><span class="sxs-lookup"><span data-stu-id="e1391-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="e1391-117">Spuštění kontejnerů bez správy serverů</span><span class="sxs-lookup"><span data-stu-id="e1391-117">Run containers without managing servers</span></span>
- <span data-ttu-id="e1391-118">Zvyšte agilitu díky kontejnerům na vyžádání</span><span class="sxs-lookup"><span data-stu-id="e1391-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="e1391-119">Nasazujte kontejnery do cloudu s nebývalou jednoduchostí a rychlostí – s jediným příkazem.</span><span class="sxs-lookup"><span data-stu-id="e1391-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="e1391-120">Bezpečné aplikace s izolací hypervisoru</span><span class="sxs-lookup"><span data-stu-id="e1391-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="e1391-121">Stručně řečeno, s ACI můžete vyvíjet aplikace rychle bez správy virtuálních počítačů nebo se museli učit nové nástroje.</span><span class="sxs-lookup"><span data-stu-id="e1391-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="e1391-122">Je to jen vaše aplikace, v kontejneru, běží v cloudu.</span><span class="sxs-lookup"><span data-stu-id="e1391-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="e1391-123">[Předchozí](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [další](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="e1391-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
