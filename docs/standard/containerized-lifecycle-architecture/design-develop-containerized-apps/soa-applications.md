---
title: Aplikace SOA
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5f60ff2fb1567d08b9e51e14ce5660a8e42f54aa
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="soa-applications"></a><span data-ttu-id="01246-103">Aplikace SOA</span><span class="sxs-lookup"><span data-stu-id="01246-103">SOA applications</span></span>

<span data-ttu-id="01246-104">SOA byl Nepromyšlené termín a určená mnoho různých věcí na jiné osoby.</span><span class="sxs-lookup"><span data-stu-id="01246-104">SOA was an overused term and meant so many different things to different people.</span></span> <span data-ttu-id="01246-105">Ale minimálně a jako běžné jmenovatel, SOA, nebo orientaci na služby, střední architektuře vaší aplikace pomocí decomposing v několika služeb (nejčastěji jako služeb HTTP), které můžou být klasifikované v různých typů struktura jako subsystémy nebo v jiných případech jako úrovně.</span><span class="sxs-lookup"><span data-stu-id="01246-105">But at a minimum and as a common denominator, SOA, or service orientation, mean that you structure the architecture of your application by decomposing it in multiple services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="01246-106">Tyto služby můžete v současné době nasadit jako Docker kontejnery, které řeší problémy související s nasazení, protože všechny závislosti jsou zahrnuty do bitové kopie kontejneru.</span><span class="sxs-lookup"><span data-stu-id="01246-106">Today, you can deploy those services as Docker containers, which solves deployment-related issues because all of the dependencies are included within the container image.</span></span> <span data-ttu-id="01246-107">Ale pokud budete potřebovat pro škálované SOAs, můžete setkat výzvy Pokud nasazujete na základě jedné instance.</span><span class="sxs-lookup"><span data-stu-id="01246-107">However, when you need to scale-out SOAs, you might encounter challenges if you are deploying based on single instances.</span></span> <span data-ttu-id="01246-108">Toto je, kde Docker, clustering softwaru nebo orchestrator vám pomůže.</span><span class="sxs-lookup"><span data-stu-id="01246-108">This is where a Docker clustering software or orchestrator will help you.</span></span> <span data-ttu-id="01246-109">Podíváme to podrobněji v další části když jsme zkontrolujte mikroslužeb přístupy.</span><span class="sxs-lookup"><span data-stu-id="01246-109">We'll look at this in greater detail in the next section when we examine microservices approaches.</span></span>

<span data-ttu-id="01246-110">Na konci dne jsou užitečné pro obě tradiční architektury SOA nebo pro pokročilejší architektura mikroslužeb, ve kterém každý mikroslužbu vlastní jeho datového modelu řešení clusteringu kontejneru.</span><span class="sxs-lookup"><span data-stu-id="01246-110">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture or for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="01246-111">A díky více databází, můžete také můžete Škálováním na více systémů datové vrstvy místo práce monolitický databáze sdílené službami SOA.</span><span class="sxs-lookup"><span data-stu-id="01246-111">And, thanks to multiple databases, you also can scale-out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="01246-112">Diskuzi o rozdělení dat je však čistě o architektuře a designu.</span><span class="sxs-lookup"><span data-stu-id="01246-112">However, the discussion about splitting the data is purely about architecture and design.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="01246-113">[Předchozí] (state-and-data-in-docker-applications.md) [Další] (orchestraci vysokou škálovatelnost availability.md)</span><span class="sxs-lookup"><span data-stu-id="01246-113">[Previous] (state-and-data-in-docker-applications.md) [Next] (orchestrate-high-scalability-availability.md)</span></span>
