---
title: Aplikace SOA
description: Pamatujte, že kontejnery můžou být také užitečnou možností nasazení pro aplikace SOA.
ms.date: 08/06/2020
ms.openlocfilehash: 5cc616eaf3be31ae704320df6ec54deed9529989
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915252"
---
# <a name="service-oriented-applications"></a><span data-ttu-id="3f8bf-103">Aplikace orientované na služby</span><span class="sxs-lookup"><span data-stu-id="3f8bf-103">Service-oriented applications</span></span>

<span data-ttu-id="3f8bf-104">Architektura typu SOA (Service-orientované) byla nepoužitým termínem, který pro různé lidi znamenal mnoho různých věcí.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-104">Service-Oriented Architecture (SOA) was an overused term that meant many different things to different people.</span></span> <span data-ttu-id="3f8bf-105">Ale jako společný jmenovatel, záznam SOA znamená, že budete strukturovat architekturu aplikace tím, že ji rozdělíte do několika služeb (nejčastěji jako služby HTTP), které je možné klasifikovat v různých typech, jako jsou subsystémy nebo v jiných případech jako vrstvy.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-105">But as a common denominator, SOA means that you structure the architecture of your application by decomposing it into several services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="3f8bf-106">V současné době můžete tyto služby nasadit jako kontejnery Docker, které řeší problémy související s nasazením, protože všechny závislosti jsou zahrnuty v imagi kontejneru.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-106">Today, you can deploy those services as Docker containers, which solve deployment-related issues because all of the dependencies are included in the container image.</span></span> <span data-ttu-id="3f8bf-107">Pokud ale potřebujete škálovat SOAs, může dojít k problémům při nasazení na základě jednotlivých instancí.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-107">However, when you need to scale out SOAs, you might encounter challenges if you're deploying based on single instances.</span></span> <span data-ttu-id="3f8bf-108">Tuto výzvu lze zpracovat pomocí softwaru Docker pro clusteringu nebo produktu Orchestrator.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-108">This challenge can be handled using Docker clustering software or an orchestrator.</span></span> <span data-ttu-id="3f8bf-109">Když prozkoumáte přístupy k mikroslužbám, bude se vám podíváme na orchestraci podrobněji v další části.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-109">You'll get to look at orchestrators in greater detail in the next section, when you explore microservices approaches.</span></span>

<span data-ttu-id="3f8bf-110">Kontejnery Docker jsou užitečné (ale nevyžadují se) pro tradiční architektury zaměřené na služby a pokročilejší architektury mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="3f8bf-111">Na konci dne jsou řešení clusteringu kontejneru užitečná pro tradiční architekturu SOA i pro pokročilejší architekturu mikroslužeb, ve které každá mikroslužba vlastní svůj datový model.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture and for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="3f8bf-112">A díky více databázím můžete také škálovat datovou vrstvu místo práce s monolitické databázemi sdílenými službami SOA.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-112">And thanks to multiple databases, you can also scale out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="3f8bf-113">Diskuze o rozdělení dat je ale čistě o architektuře a návrhu.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3f8bf-114">[Předchozí](state-and-data-in-docker-applications.md) 
> [Další](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="3f8bf-114">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>
