---
title: Aplikace SOA
description: Berte v úvahu, že kontejnery můžou být také možnost užitečné nasazení pro aplikace SOA.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 353ba738143b7dcd92c7c75ac27ea6a7370f9da6
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745830"
---
# <a name="service-oriented-applications"></a><span data-ttu-id="4a7b8-103">Aplikace orientované na služby</span><span class="sxs-lookup"><span data-stu-id="4a7b8-103">Service-oriented applications</span></span>

<span data-ttu-id="4a7b8-104">Architektura orientovaná na služby (záznam SOA) byl Nepromyšlené termín, který určená mnoho různé věci pro různé osoby.</span><span class="sxs-lookup"><span data-stu-id="4a7b8-104">Service-Oriented Architecture (SOA) was an overused term that meant many different things to different people.</span></span> <span data-ttu-id="4a7b8-105">Ale jako společným faktorem SOA znamená, že struktury architekturu aplikace podle rozložení na několik služeb (nejčastěji jako služeb HTTP), které můžou být klasifikované v různých typech, jako je subsystémy nebo v jiných případech, jako úrovně.</span><span class="sxs-lookup"><span data-stu-id="4a7b8-105">But as a common denominator, SOA means that you structure the architecture of your application by decomposing it into several services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="4a7b8-106">Tyto služby ještě dnes, můžete nasadit jako kontejnery Dockeru, které vzhledem k tomu, že všechny závislosti jsou součástí image kontejneru s řešením problémů souvisejících s nasazením.</span><span class="sxs-lookup"><span data-stu-id="4a7b8-106">Today, you can deploy those services as Docker containers, which solve deployment-related issues because all of the dependencies are included in the container image.</span></span> <span data-ttu-id="4a7b8-107">Ale pokud potřebujete horizontálně navýšit kapacitu SOAs, může dojít výzvy Pokud provádíte nasazení na základě jedné instance.</span><span class="sxs-lookup"><span data-stu-id="4a7b8-107">However, when you need to scale out SOAs, you might encounter challenges if you are deploying based on single instances.</span></span> <span data-ttu-id="4a7b8-108">Tento problém možné je zpracovávat pomocí Dockeru clustering softwaru nebo produktu orchestrator.</span><span class="sxs-lookup"><span data-stu-id="4a7b8-108">This challenge can be handled using Docker clustering software or an orchestrator.</span></span> <span data-ttu-id="4a7b8-109">Podíváme na orchestrátory podrobněji v další části, když se podíváme na mikroslužby přístupy.</span><span class="sxs-lookup"><span data-stu-id="4a7b8-109">We'll look at orchestrators in greater detail in the next section, when we explore microservices approaches.</span></span>

<span data-ttu-id="4a7b8-110">Kontejnery dockeru jsou užitečné (ale nevyžadováno) pro tradiční architektury orientované na služby a pokročilejší architekturu mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="4a7b8-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="4a7b8-111">Na konci dne jsou užitečné pro obě tradiční architektura SOA a pro pokročilejší architekturu mikroslužeb, ve kterém je vlastníkem jednotlivých mikroslužeb její datový model clusteringu řešení kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="4a7b8-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture and for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="4a7b8-112">A díky více databází, také můžete škálovat datovou vrstvu, místo abyste pracovali s monolitické databází sdílí služby SOA.</span><span class="sxs-lookup"><span data-stu-id="4a7b8-112">And thanks to multiple databases, you also can scale out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="4a7b8-113">Diskuze o rozdělení dat je však čistě o architektuře a designu.</span><span class="sxs-lookup"><span data-stu-id="4a7b8-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4a7b8-114">[Předchozí](state-and-data-in-docker-applications.md)
>[další](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="4a7b8-114">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>
