---
title: Aplikace SOA
description: "Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 81d2b60303e051568b664ec20225d835a09187c0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="soa-applications"></a><span data-ttu-id="73e7d-104">Aplikace SOA</span><span class="sxs-lookup"><span data-stu-id="73e7d-104">SOA applications</span></span>

<span data-ttu-id="73e7d-105">SOA byl Nepromyšlené termín a určená mnoho různých věcí na jiné osoby.</span><span class="sxs-lookup"><span data-stu-id="73e7d-105">SOA was an overused term and meant so many different things to different people.</span></span> <span data-ttu-id="73e7d-106">Ale minimálně a jako běžné jmenovatel, SOA, nebo orientaci na služby, střední architektuře vaší aplikace pomocí decomposing v několika služeb (nejčastěji jako služeb HTTP), které můžou být klasifikované v různých typů struktura jako subsystémy nebo v jiných případech jako úrovně.</span><span class="sxs-lookup"><span data-stu-id="73e7d-106">But at a minimum and as a common denominator, SOA, or service orientation, mean that you structure the architecture of your application by decomposing it in multiple services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="73e7d-107">Tyto služby můžete v současné době nasadit jako Docker kontejnery, které řeší problémy související s nasazení, protože všechny závislosti jsou zahrnuty do bitové kopie kontejneru.</span><span class="sxs-lookup"><span data-stu-id="73e7d-107">Today, you can deploy those services as Docker containers, which solves deployment-related issues because all of the dependencies are included within the container image.</span></span> <span data-ttu-id="73e7d-108">Ale pokud budete potřebovat pro škálované SOAs, můžete setkat výzvy Pokud nasazujete na základě jedné instance.</span><span class="sxs-lookup"><span data-stu-id="73e7d-108">However, when you need to scale-out SOAs, you might encounter challenges if you are deploying based on single instances.</span></span> <span data-ttu-id="73e7d-109">Toto je, kde Docker, clustering softwaru nebo orchestrator vám pomůže.</span><span class="sxs-lookup"><span data-stu-id="73e7d-109">This is where a Docker clustering software or orchestrator will help you.</span></span> <span data-ttu-id="73e7d-110">Podíváme to podrobněji v další části když jsme zkontrolujte mikroslužeb přístupy.</span><span class="sxs-lookup"><span data-stu-id="73e7d-110">We'll look at this in greater detail in the next section when we examine microservices approaches.</span></span>

<span data-ttu-id="73e7d-111">Na konci dne jsou užitečné pro obě tradiční architektury SOA nebo pro pokročilejší architektura mikroslužeb, ve kterém každý mikroslužbu vlastní jeho datového modelu řešení clusteringu kontejneru.</span><span class="sxs-lookup"><span data-stu-id="73e7d-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture or for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="73e7d-112">A díky více databází, můžete také můžete Škálováním na více systémů datové vrstvy místo práce monolitický databáze sdílené službami SOA.</span><span class="sxs-lookup"><span data-stu-id="73e7d-112">And, thanks to multiple databases, you also can scale-out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="73e7d-113">Diskuzi o rozdělení dat je však čistě o architektuře a designu.</span><span class="sxs-lookup"><span data-stu-id="73e7d-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="73e7d-114">[Předchozí] (state-and-data-in-docker-applications.md) [Další] (orchestraci vysokou škálovatelnost availability.md)</span><span class="sxs-lookup"><span data-stu-id="73e7d-114">[Previous] (state-and-data-in-docker-applications.md) [Next] (orchestrate-high-scalability-availability.md)</span></span>
