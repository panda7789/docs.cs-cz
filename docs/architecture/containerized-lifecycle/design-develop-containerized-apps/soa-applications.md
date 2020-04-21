---
title: Aplikace SOA
description: Mějte na paměti, že kontejnery mohou být také užitečnou možností nasazení pro aplikace SOA.
ms.date: 02/15/2019
ms.openlocfilehash: f8619cb50a7d90b911db9ff2c8ef37c3c5fde210
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738389"
---
# <a name="service-oriented-applications"></a><span data-ttu-id="7c86a-103">Aplikace orientované na služby</span><span class="sxs-lookup"><span data-stu-id="7c86a-103">Service-oriented applications</span></span>

<span data-ttu-id="7c86a-104">Architektura orientovaná na služby (SOA) byla nadměrně používaný termín, který znamenal pro různé lidi mnoho různých věcí.</span><span class="sxs-lookup"><span data-stu-id="7c86a-104">Service-Oriented Architecture (SOA) was an overused term that meant many different things to different people.</span></span> <span data-ttu-id="7c86a-105">Ale jako společný jmenovatel SOA znamená, že strukturu architektury aplikace rozkladu do několika služeb (nejčastěji jako služby HTTP), které mohou být klasifikovány v různých typech, jako jsou subsystémy nebo v jiných případech jako vrstvy.</span><span class="sxs-lookup"><span data-stu-id="7c86a-105">But as a common denominator, SOA means that you structure the architecture of your application by decomposing it into several services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="7c86a-106">Dnes můžete nasadit tyto služby jako kontejnery Dockeru, které řeší problémy související s nasazením, protože všechny závislosti jsou zahrnuty v image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="7c86a-106">Today, you can deploy those services as Docker containers, which solve deployment-related issues because all of the dependencies are included in the container image.</span></span> <span data-ttu-id="7c86a-107">Však když potřebujete horizontální navýšení kapacity SOA, můžete se setkat s problémy, pokud nasazujete na základě jednotlivých instancí.</span><span class="sxs-lookup"><span data-stu-id="7c86a-107">However, when you need to scale out SOAs, you might encounter challenges if you're deploying based on single instances.</span></span> <span data-ttu-id="7c86a-108">Tuto výzvu lze zpracovat pomocí softwaru clusteringdockeru nebo orchestrátoru.</span><span class="sxs-lookup"><span data-stu-id="7c86a-108">This challenge can be handled using Docker clustering software or an orchestrator.</span></span> <span data-ttu-id="7c86a-109">Podíváme se na orchestrátory podrobněji v další části, když prozkoumáme přístupy mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="7c86a-109">We'll look at orchestrators in greater detail in the next section, when we explore microservices approaches.</span></span>

<span data-ttu-id="7c86a-110">Kontejnery Dockeru jsou užitečné (ale není vyžadováno) pro tradiční architektury orientované na služby a pokročilejší architektury mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="7c86a-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="7c86a-111">Na konci dne řešení clustering kontejnerů jsou užitečné pro tradiční soa architektury a pro pokročilejší architekturu mikroslužeb, ve kterém každý mikroslužby vlastní svůj datový model.</span><span class="sxs-lookup"><span data-stu-id="7c86a-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture and for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="7c86a-112">A díky více databázím můžete také škálovat datovou vrstvu namísto práce s monolitickými databázemi sdílenými službami SOA.</span><span class="sxs-lookup"><span data-stu-id="7c86a-112">And thanks to multiple databases, you can also scale out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="7c86a-113">Diskuse o rozdělení dat je však čistě o architektuře a designu.</span><span class="sxs-lookup"><span data-stu-id="7c86a-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7c86a-114">[Předchozí](state-and-data-in-docker-applications.md)
>[další](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="7c86a-114">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>
