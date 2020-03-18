---
title: Aplikace SOA
description: Mějte na paměti, že kontejnery mohou být také užitečnou možností nasazení pro aplikace SOA.
ms.date: 02/15/2019
ms.openlocfilehash: aa56ada7b14a465fb3dafd02b03b815782ac765b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295273"
---
# <a name="service-oriented-applications"></a><span data-ttu-id="18e1c-103">Aplikace orientované na služby</span><span class="sxs-lookup"><span data-stu-id="18e1c-103">Service-oriented applications</span></span>

<span data-ttu-id="18e1c-104">Architektura orientovaná na služby (SOA) byla nadměrně používaný termín, který znamenal pro různé lidi mnoho různých věcí.</span><span class="sxs-lookup"><span data-stu-id="18e1c-104">Service-Oriented Architecture (SOA) was an overused term that meant many different things to different people.</span></span> <span data-ttu-id="18e1c-105">Ale jako společný jmenovatel SOA znamená, že strukturu architektury aplikace rozkladu do několika služeb (nejčastěji jako služby HTTP), které mohou být klasifikovány v různých typech, jako jsou subsystémy nebo v jiných případech jako vrstvy.</span><span class="sxs-lookup"><span data-stu-id="18e1c-105">But as a common denominator, SOA means that you structure the architecture of your application by decomposing it into several services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="18e1c-106">Dnes můžete nasadit tyto služby jako kontejnery Dockeru, které řeší problémy související s nasazením, protože všechny závislosti jsou zahrnuty v image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="18e1c-106">Today, you can deploy those services as Docker containers, which solve deployment-related issues because all of the dependencies are included in the container image.</span></span> <span data-ttu-id="18e1c-107">Však když potřebujete horizontální navýšení kapacity SOA, můžete se setkat s problémy, pokud nasazujete na základě jednotlivých instancí.</span><span class="sxs-lookup"><span data-stu-id="18e1c-107">However, when you need to scale out SOAs, you might encounter challenges if you're deploying based on single instances.</span></span> <span data-ttu-id="18e1c-108">Tuto výzvu lze zpracovat pomocí softwaru clusteringdockeru nebo orchestrátoru.</span><span class="sxs-lookup"><span data-stu-id="18e1c-108">This challenge can be handled using Docker clustering software or an orchestrator.</span></span> <span data-ttu-id="18e1c-109">Podíváme se na orchestrátory podrobněji v další části, když prozkoumáme přístupy mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="18e1c-109">We'll look at orchestrators in greater detail in the next section, when we explore microservices approaches.</span></span>

<span data-ttu-id="18e1c-110">Kontejnery Dockeru jsou užitečné (ale není vyžadováno) pro tradiční architektury orientované na služby a pokročilejší architektury mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="18e1c-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="18e1c-111">Na konci dne řešení clustering kontejnerů jsou užitečné pro tradiční soa architektury a pro pokročilejší architekturu mikroslužeb, ve kterém každý mikroslužby vlastní svůj datový model.</span><span class="sxs-lookup"><span data-stu-id="18e1c-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture and for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="18e1c-112">A díky více databázím můžete také škálovat datovou vrstvu namísto práce s monolitickými databázemi sdílenými službami SOA.</span><span class="sxs-lookup"><span data-stu-id="18e1c-112">And thanks to multiple databases, you also can scale out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="18e1c-113">Diskuse o rozdělení dat je však čistě o architektuře a designu.</span><span class="sxs-lookup"><span data-stu-id="18e1c-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="18e1c-114">[Předchozí](state-and-data-in-docker-applications.md)
>[další](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="18e1c-114">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>
