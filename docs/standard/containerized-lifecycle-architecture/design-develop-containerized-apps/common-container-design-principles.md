---
title: Běžné zásady návrhu kontejneru
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 3af174279e8b6f56a10413817b05ef68cfcabea5
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50202171"
---
# <a name="common-container-design-principles"></a><span data-ttu-id="72194-103">Běžné zásady návrhu kontejneru</span><span class="sxs-lookup"><span data-stu-id="72194-103">Common container design principles</span></span>

<span data-ttu-id="72194-104">Dopředu získání do procesu vývoje existuje pár základních konceptů stojí za zmínku s ohledem na použití kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="72194-104">Ahead of getting into the development process there are a few basic concepts worth mentioning with regard to how you use containers.</span></span>

## <a name="container-equals-a-process"></a><span data-ttu-id="72194-105">Kontejner se rovná procesu</span><span class="sxs-lookup"><span data-stu-id="72194-105">Container equals a process</span></span>

<span data-ttu-id="72194-106">V kontejneru modelu kontejner představuje jeden proces.</span><span class="sxs-lookup"><span data-stu-id="72194-106">In the container model, a container represents a single process.</span></span> <span data-ttu-id="72194-107">Definuje kontejner jako hranice procesu, začněte vytvářet primitivy používá k škálování, nebo vypnutí dávkové procesy.</span><span class="sxs-lookup"><span data-stu-id="72194-107">By defining a container as a process boundary, you begin to create the primitives used to scale, or batch-off, processes.</span></span> <span data-ttu-id="72194-108">Při spuštění kontejneru Dockeru, zobrazí se vám [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) definice.</span><span class="sxs-lookup"><span data-stu-id="72194-108">When you run a Docker container, you'll see an [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) definition.</span></span> <span data-ttu-id="72194-109">Definuje procesu a životnosti kontejneru.</span><span class="sxs-lookup"><span data-stu-id="72194-109">This defines the process and the lifetime of the container.</span></span> <span data-ttu-id="72194-110">Po dokončení procesu kontejneru životní cyklus se ukončí.</span><span class="sxs-lookup"><span data-stu-id="72194-110">When the process completes, the container life cycle ends.</span></span> <span data-ttu-id="72194-111">Dlouho běžící procesy, jako jsou webové servery a krátkodobou procesy, jako jsou dávkové úlohy, které mohou u je implementovaná jako Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/).</span><span class="sxs-lookup"><span data-stu-id="72194-111">There are long-running processes, such as web servers, and short-lived processes, such as batch jobs, which might have been implemented as Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/).</span></span> <span data-ttu-id="72194-112">Pokud proces selže, konce kontejneru a orchestrátor převezme.</span><span class="sxs-lookup"><span data-stu-id="72194-112">If the process fails, the container ends, and the orchestrator takes over.</span></span> <span data-ttu-id="72194-113">Pokud orchestrátoru dostal zachovat spuštěných 5 instancí a jeden server selže, vytvoří orchestrátoru jiný kontejner k nahrazení procesu, který selhal.</span><span class="sxs-lookup"><span data-stu-id="72194-113">If the orchestrator was instructed to keep five instances running and one fails, the orchestrator will create another container to replace the failed process.</span></span> <span data-ttu-id="72194-114">V rámci úlohy služby batch je proces spuštěn s parametry.</span><span class="sxs-lookup"><span data-stu-id="72194-114">In a batch job, the process is started with parameters.</span></span> <span data-ttu-id="72194-115">Po dokončení procesu je práce dokončena.</span><span class="sxs-lookup"><span data-stu-id="72194-115">When the process completes, the work is complete.</span></span>

<span data-ttu-id="72194-116">Může pro vás scénář, ve kterém chcete více procesů spuštěných ve jedním kontejnerem.</span><span class="sxs-lookup"><span data-stu-id="72194-116">You might find a scenario in which you want multiple processes running in a single container.</span></span> <span data-ttu-id="72194-117">V libovolném dokumentu architektura neexistuje nikdy "," ani není vždy na "always".</span><span class="sxs-lookup"><span data-stu-id="72194-117">In any architecture document, there's never a "never," nor is there always an "always."</span></span> <span data-ttu-id="72194-118">Pro scénáře, které vyžadují více procesů, je použít běžný vzor [Supervisor](http://supervisord.org/).</span><span class="sxs-lookup"><span data-stu-id="72194-118">For scenarios requiring multiple processes, a common pattern is to use [Supervisor](http://supervisord.org/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="72194-119">[Předchozí](design-docker-applications.md)
[další](monolithic-applications.md)</span><span class="sxs-lookup"><span data-stu-id="72194-119">[Previous](design-docker-applications.md)
[Next](monolithic-applications.md)</span></span>
