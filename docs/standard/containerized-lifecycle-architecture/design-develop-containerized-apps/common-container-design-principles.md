---
title: "Běžné zásady designu kontejneru"
description: "Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a9cd569a931824c4fab060b99265ea9e3ca75129
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="common-container-design-principles"></a><span data-ttu-id="7f605-104">Běžné zásady designu kontejneru</span><span class="sxs-lookup"><span data-stu-id="7f605-104">Common container design principles</span></span>

<span data-ttu-id="7f605-105">Článek získání do procesu vývoje existuje pár základních konceptech důležité zmínit, s ohledem na tom, jak používáte kontejnery.</span><span class="sxs-lookup"><span data-stu-id="7f605-105">Ahead of getting into the development process there are a few basic concepts worth mentioning with regard to how you use containers.</span></span>

## <a name="container-equals-a-process"></a><span data-ttu-id="7f605-106">Kontejner se rovná proces</span><span class="sxs-lookup"><span data-stu-id="7f605-106">Container equals a process</span></span>

<span data-ttu-id="7f605-107">V kontejneru modelu kontejner představuje jeden proces.</span><span class="sxs-lookup"><span data-stu-id="7f605-107">In the container model, a container represents a single process.</span></span> <span data-ttu-id="7f605-108">Definováním kontejner jako hranice procesu začnete vytvářet primitiv umožňuje škálování, nebo batch – vypnuté, procesy.</span><span class="sxs-lookup"><span data-stu-id="7f605-108">By defining a container as a process boundary, you begin to create the primitives used to scale, or batch-off, processes.</span></span> <span data-ttu-id="7f605-109">Když spustíte kontejner Docker, uvidíte [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) definice.</span><span class="sxs-lookup"><span data-stu-id="7f605-109">When you run a Docker container, you'll see an [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) definition.</span></span> <span data-ttu-id="7f605-110">Definuje proces a dobu života kontejneru.</span><span class="sxs-lookup"><span data-stu-id="7f605-110">This defines the process and the lifetime of the container.</span></span> <span data-ttu-id="7f605-111">Po dokončení procesu životní cyklus kontejneru se ukončí.</span><span class="sxs-lookup"><span data-stu-id="7f605-111">When the process completes, the container life cycle ends.</span></span> <span data-ttu-id="7f605-112">Existují dlouho běžící procesy, jako jsou webové servery a krátkodobou procesy, jako je třeba dávkové úlohy, které může je implementovaná jako Microsoft Azure [WebJobs](https://azure.microsoft.com/en-us/documentation/articles/websites-webjobs-resources/).</span><span class="sxs-lookup"><span data-stu-id="7f605-112">There are long-running processes, such as web servers, and short-lived processes, such as batch jobs, which might have been implemented as Microsoft Azure [WebJobs](https://azure.microsoft.com/en-us/documentation/articles/websites-webjobs-resources/).</span></span> <span data-ttu-id="7f605-113">Pokud proces selže, elementy end kontejneru a orchestrator má.</span><span class="sxs-lookup"><span data-stu-id="7f605-113">If the process fails, the container ends, and the orchestrator takes over.</span></span> <span data-ttu-id="7f605-114">Pokud orchestrator dostal pokyny pro udržování pět instancí spuštěných a jeden server selže, vytvoří orchestrator jiný kontejner nahradit selhal proces.</span><span class="sxs-lookup"><span data-stu-id="7f605-114">If the orchestrator was instructed to keep five instances running and one fails, the orchestrator will create another container to replace the failed process.</span></span> <span data-ttu-id="7f605-115">V rámci úlohy batch je proces spuštěn s parametry.</span><span class="sxs-lookup"><span data-stu-id="7f605-115">In a batch job, the process is started with parameters.</span></span> <span data-ttu-id="7f605-116">Po dokončení procesu, práce je dokončena.</span><span class="sxs-lookup"><span data-stu-id="7f605-116">When the process completes, the work is complete.</span></span>

<span data-ttu-id="7f605-117">Můžete se setkat scénář, ve kterém má více procesů spuštěných ve jediný kontejner.</span><span class="sxs-lookup"><span data-stu-id="7f605-117">You might find a scenario in which you want multiple processes running in a single container.</span></span> <span data-ttu-id="7f605-118">V dokumentu architektury, se nikdy "nikdy," ani je k dispozici vždy na "vždy".</span><span class="sxs-lookup"><span data-stu-id="7f605-118">In any architecture document, there's never a "never," nor is there always an "always."</span></span> <span data-ttu-id="7f605-119">Pro scénáře, které vyžadují více procesů, je použít běžný vzor [nadřízeného](http://supervisord.org/).</span><span class="sxs-lookup"><span data-stu-id="7f605-119">For scenarios requiring multiple processes, a common pattern is to use [Supervisor](http://supervisord.org/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="7f605-120">[Předchozí] (návrhu docker-applications.md) [Další] (monolitický applications.md)</span><span class="sxs-lookup"><span data-stu-id="7f605-120">[Previous] (design-docker-applications.md) [Next] (monolithic-applications.md)</span></span>
