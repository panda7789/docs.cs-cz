---
title: Odolnost nativní pro cloud
description: Architekt cloudových nativních aplikací .NET pro Azure | Nativní odolnost cloudu
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: f3aa89e3ae21b13a31f65013b59636b3f931553c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613769"
---
# <a name="cloud-native-resiliency"></a><span data-ttu-id="92166-103">Odolnost nativní pro cloud</span><span class="sxs-lookup"><span data-stu-id="92166-103">Cloud-native resiliency</span></span>

<span data-ttu-id="92166-104">Odolnost proti chybám je schopnost systému reagovat na selhání a pořád zůstává funkční.</span><span class="sxs-lookup"><span data-stu-id="92166-104">Resiliency is the ability of your system to react to failure and still remain functional.</span></span> <span data-ttu-id="92166-105">Nejedná se o předcházení chybám, ale přijímá selhání a sestavuje vaše cloudové nativní služby, aby na ně reagovaly.</span><span class="sxs-lookup"><span data-stu-id="92166-105">It's not about avoiding failure, but accepting failure and constructing your cloud-native services to respond to it.</span></span> <span data-ttu-id="92166-106">Chcete se rychle vrátit do plně funkčního stavu.</span><span class="sxs-lookup"><span data-stu-id="92166-106">You want to return to a fully functioning state quickly as possible.</span></span>

<span data-ttu-id="92166-107">Na rozdíl od tradičních aplikací monolitické, kde všechno běží společně v jednom procesu, cloudové systémy pro Cloud využívají distribuovanou architekturu, jak je znázorněno na obrázku 6-1:</span><span class="sxs-lookup"><span data-stu-id="92166-107">Unlike traditional monolithic applications, where everything runs together in a single process, cloud-native systems embrace a distributed architecture as shown in Figure 6-1:</span></span>

![Distribuované cloudové prostředí – nativní](./media/distributed-cloud-native-environment.png)

<span data-ttu-id="92166-109">**Obrázek 6-1.**</span><span class="sxs-lookup"><span data-stu-id="92166-109">**Figure 6-1.**</span></span> <span data-ttu-id="92166-110">Distribuované cloudové prostředí – nativní</span><span class="sxs-lookup"><span data-stu-id="92166-110">Distributed cloud-native environment</span></span>

<span data-ttu-id="92166-111">Na předchozím obrázku se každá mikroslužba a cloudová [Služba](https://12factor.net/backing-services) provádí v samostatném procesu v rámci serverové infrastruktury a komunikuje prostřednictvím síťových volání.</span><span class="sxs-lookup"><span data-stu-id="92166-111">In the previous figure, each microservice and cloud-based [backing service](https://12factor.net/backing-services) execute in a separate process, across server infrastructure, communicating via network-based calls.</span></span>

<span data-ttu-id="92166-112">Provoz v tomto prostředí musí být citlivý na mnoho různých výzev:</span><span class="sxs-lookup"><span data-stu-id="92166-112">Operating in this environment, a service must be sensitive to many different challenges:</span></span>

- <span data-ttu-id="92166-113">Neočekávaná latence sítě – čas, kdy se žádost o službu dopravuje na příjemce a zpátky.</span><span class="sxs-lookup"><span data-stu-id="92166-113">Unexpected network latency - the time for a service request to travel to the receiver and back.</span></span>

- <span data-ttu-id="92166-114">[Přechodné chyby](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) – krátkodobé chyby připojení k síti</span><span class="sxs-lookup"><span data-stu-id="92166-114">[Transient faults](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) - short-lived network connectivity errors.</span></span>

- <span data-ttu-id="92166-115">Zablokování dlouhodobě spuštěnou synchronní operací.</span><span class="sxs-lookup"><span data-stu-id="92166-115">Blockage by a long-running synchronous operation.</span></span>

- <span data-ttu-id="92166-116">Hostitelský proces, u kterého došlo k chybě a probíhá restartování nebo přesunutí.</span><span class="sxs-lookup"><span data-stu-id="92166-116">A host process that has crashed and is being restarted or moved.</span></span>

- <span data-ttu-id="92166-117">Přetížená mikroslužba, která nemůže reagovat po krátkou dobu.</span><span class="sxs-lookup"><span data-stu-id="92166-117">An overloaded microservice that can't respond for a short time.</span></span>

- <span data-ttu-id="92166-118">Provozní operace nástroje Orchestrator, jako je například postupná inovace nebo přesunutí služby z jednoho uzlu do jiného.</span><span class="sxs-lookup"><span data-stu-id="92166-118">An in-flight orchestrator operation such as a rolling upgrade or moving a service from one node to another.</span></span>

- <span data-ttu-id="92166-119">Selhání hardwaru.</span><span class="sxs-lookup"><span data-stu-id="92166-119">Hardware failures.</span></span>

<span data-ttu-id="92166-120">Cloudové platformy můžou detekovat a zmírnit mnohé z těchto potíží s infrastrukturou.</span><span class="sxs-lookup"><span data-stu-id="92166-120">Cloud platforms can detect and mitigate many of these infrastructure issues.</span></span> <span data-ttu-id="92166-121">Může se restartovat, škálovat a dokonce znovu distribuovat službu do jiného uzlu.</span><span class="sxs-lookup"><span data-stu-id="92166-121">It may restart, scale out, and even redistribute your service to a different node.</span></span>  <span data-ttu-id="92166-122">Abyste ale mohli plně využít této integrované ochrany, musíte navrhnout vaše služby, aby na ně reagovaly a i v tomto dynamickém prostředí.</span><span class="sxs-lookup"><span data-stu-id="92166-122">However, to take full advantage of this built-in protection, you must design your services to react to it and thrive in this dynamic environment.</span></span>

<span data-ttu-id="92166-123">V následujících částech budeme zkoumat techniky obrannou linií, které vaše služba a spravované cloudové prostředky můžou využít k minimalizaci výpadků a přerušení.</span><span class="sxs-lookup"><span data-stu-id="92166-123">In the following sections, we'll explore defensive techniques that your service and managed cloud resources can leverage to minimize downtime and disruption.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="92166-124">[Předchozí](elastic-search-in-azure.md) 
> [Další](application-resiliency-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="92166-124">[Previous](elastic-search-in-azure.md)
[Next](application-resiliency-patterns.md)</span></span>
