---
title: Odolnost nativní pro cloud
description: Architekt cloudových nativních aplikací .NET pro Azure | Nativní odolnost cloudu
ms.date: 06/30/2019
ms.openlocfilehash: 427405d95534c4467ab519c2188fe88e2f18e2b2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781088"
---
# <a name="cloud-native-resiliency"></a><span data-ttu-id="6160d-103">Odolnost nativní pro cloud</span><span class="sxs-lookup"><span data-stu-id="6160d-103">Cloud-native resiliency</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="6160d-104">Odolnost proti chybám je schopnost systému reagovat na selhání a pořád zůstává funkční.</span><span class="sxs-lookup"><span data-stu-id="6160d-104">Resiliency is the ability of your system to react to failure and still remain functional.</span></span> <span data-ttu-id="6160d-105">Nejedná se o předcházení selhání.</span><span class="sxs-lookup"><span data-stu-id="6160d-105">It isn't about avoiding failure.</span></span> <span data-ttu-id="6160d-106">Ale jedná se o přijetí této chyby v cloudových systémech a sestavení vaší aplikace, která na ni reaguje.</span><span class="sxs-lookup"><span data-stu-id="6160d-106">But it's about accepting that failure is inevitable in cloud-based systems and building your application to respond to it.</span></span> <span data-ttu-id="6160d-107">Koncovým cílem odolnosti proti chybám je vrácení aplikace do plně funkčního stavu po selhání.</span><span class="sxs-lookup"><span data-stu-id="6160d-107">The end-goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="6160d-108">Na rozdíl od tradičních aplikací monolitické, kde se všechno souběžně používá v jednom procesu, nativní systémy pro Cloud využívají distribuovanou architekturu, jak je znázorněno na obrázku 6-1:</span><span class="sxs-lookup"><span data-stu-id="6160d-108">Unlike traditional monolithic applications, where everything runs together in a single process, cloud-native systems embrace distributed architecture as shown in Figure 6-1:</span></span>

![Distribuované cloudové prostředí – nativní](./media/distributed-cloud-native-environment.png)

<span data-ttu-id="6160d-110">**Obrázek 6-1.**</span><span class="sxs-lookup"><span data-stu-id="6160d-110">**Figure 6-1.**</span></span> <span data-ttu-id="6160d-111">Distribuované cloudové prostředí – nativní</span><span class="sxs-lookup"><span data-stu-id="6160d-111">Distributed cloud-native environment</span></span>

<span data-ttu-id="6160d-112">Na předchozím obrázku si všimněte, že každý klient, mikroslužba a cloudová [Služba](https://12factor.net/backing-services) se spouští jako samostatný proces, který běží na různých serverech, a to prostřednictvím síťových volání.</span><span class="sxs-lookup"><span data-stu-id="6160d-112">In the previous figure, note how each client, microservice, and cloud-based [backing service](https://12factor.net/backing-services) executes as a separate process, running across different servers, all communicating via network-based calls.</span></span>

<span data-ttu-id="6160d-113">Co by to stalo špatné?</span><span class="sxs-lookup"><span data-stu-id="6160d-113">So, what could go wrong?</span></span>

- <span data-ttu-id="6160d-114">Neočekávaná [latence sítě](https://www.techopedia.com/definition/8553/network-latency).</span><span class="sxs-lookup"><span data-stu-id="6160d-114">Unexpected [network latency](https://www.techopedia.com/definition/8553/network-latency).</span></span>
- <span data-ttu-id="6160d-115">[Přechodné](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) chyby (dočasné chyby připojení k síti).</span><span class="sxs-lookup"><span data-stu-id="6160d-115">[Transient faults](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) (temporary network connectivity errors).</span></span>
- <span data-ttu-id="6160d-116">Blokuje dlouhodobě běžící synchronní operace.</span><span class="sxs-lookup"><span data-stu-id="6160d-116">Blocking by a long-running synchronous operation.</span></span>
- <span data-ttu-id="6160d-117">Hostitelský proces, u kterého došlo k chybě a probíhá restartování nebo přesunutí.</span><span class="sxs-lookup"><span data-stu-id="6160d-117">A host process that has crashed and is being restarted or moved.</span></span>
- <span data-ttu-id="6160d-118">Přetížená mikroslužba, která nemůže reagovat po krátkou dobu.</span><span class="sxs-lookup"><span data-stu-id="6160d-118">An overloaded microservice that can't respond for a short time.</span></span>
- <span data-ttu-id="6160d-119">DevOps operace, jako je například operace aktualizace nebo škálování.</span><span class="sxs-lookup"><span data-stu-id="6160d-119">An in-flight DevOps operation such as an update or scaling operation.</span></span>
- <span data-ttu-id="6160d-120">Operace nástroje Orchestrator, jako je například přesunutí služby z jednoho uzlu do jiného.</span><span class="sxs-lookup"><span data-stu-id="6160d-120">An Orchestrator operation such as moving a service from one node to another.</span></span>
- <span data-ttu-id="6160d-121">Selhání hardwaru z komoditního hardwaru.</span><span class="sxs-lookup"><span data-stu-id="6160d-121">Hardware failures from commodity hardware.</span></span>

<span data-ttu-id="6160d-122">Při nasazování distribuovaných služeb do cloudové infrastruktury se faktory z předchozího seznamu stanou velmi reálné a Vy musíte architekt a vývoj defensively, abyste s nimi mohli pracovat.</span><span class="sxs-lookup"><span data-stu-id="6160d-122">When deploying distributed services into cloud-based infrastructure, the factors from the previous list become very real and you must architect and develop defensively to deal with them.</span></span>

<span data-ttu-id="6160d-123">V malém distribuovaném systému bude selhání méně časté, ale při horizontálním navýšení kapacity můžete očekávat větší množství těchto potíží s bodem, kde se částečné selhání změní do normálního provozu.</span><span class="sxs-lookup"><span data-stu-id="6160d-123">In a small-scale distributed system, failure will be less frequent, but as a system scales up and out, you can expect to experience more of these issues to a point where partial failure becomes normal operation.</span></span>

<span data-ttu-id="6160d-124">Proto musí být vaše aplikace a infrastruktura odolné.</span><span class="sxs-lookup"><span data-stu-id="6160d-124">Therefore, your application and infrastructure must be resilient.</span></span> <span data-ttu-id="6160d-125">V následujících částech si probereme techniky obrannou linií, které můžete přidat do své aplikace a integrované funkce cloudu, které vám pomůžou s odrážkami v uživatelském prostředí.</span><span class="sxs-lookup"><span data-stu-id="6160d-125">In the following sections, we'll explore defensive techniques that you can add to your application and built-in cloud features that you can leverage to help bullet-proof your user's experience.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6160d-126">[Předchozí](elastic-search-in-azure.md)
>[Další](application-resiliency-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="6160d-126">[Previous](elastic-search-in-azure.md)
[Next](application-resiliency-patterns.md)</span></span>
