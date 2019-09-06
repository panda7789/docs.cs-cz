---
title: Aplikace SOA
description: Pamatujte, že kontejnery můžou být také užitečnou možností nasazení pro aplikace SOA.
ms.date: 02/15/2019
ms.openlocfilehash: aa56ada7b14a465fb3dafd02b03b815782ac765b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295273"
---
# <a name="service-oriented-applications"></a><span data-ttu-id="c7e45-103">Aplikace orientované na služby</span><span class="sxs-lookup"><span data-stu-id="c7e45-103">Service-oriented applications</span></span>

<span data-ttu-id="c7e45-104">Architektura typu SOA (Service-orientované) byla nepoužitým termínem, který pro různé lidi znamenal mnoho různých věcí.</span><span class="sxs-lookup"><span data-stu-id="c7e45-104">Service-Oriented Architecture (SOA) was an overused term that meant many different things to different people.</span></span> <span data-ttu-id="c7e45-105">Ale jako společný jmenovatel, záznam SOA znamená, že budete strukturovat architekturu aplikace tím, že ji rozdělíte do několika služeb (nejčastěji jako služby HTTP), které je možné klasifikovat v různých typech, jako jsou subsystémy nebo v jiných případech jako vrstvy.</span><span class="sxs-lookup"><span data-stu-id="c7e45-105">But as a common denominator, SOA means that you structure the architecture of your application by decomposing it into several services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="c7e45-106">V současné době můžete tyto služby nasadit jako kontejnery Docker, které řeší problémy související s nasazením, protože všechny závislosti jsou zahrnuty v imagi kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c7e45-106">Today, you can deploy those services as Docker containers, which solve deployment-related issues because all of the dependencies are included in the container image.</span></span> <span data-ttu-id="c7e45-107">Pokud ale potřebujete škálovat SOAs, může dojít k problémům při nasazení na základě jednotlivých instancí.</span><span class="sxs-lookup"><span data-stu-id="c7e45-107">However, when you need to scale out SOAs, you might encounter challenges if you're deploying based on single instances.</span></span> <span data-ttu-id="c7e45-108">Tuto výzvu lze zpracovat pomocí softwaru Docker pro clusteringu nebo produktu Orchestrator.</span><span class="sxs-lookup"><span data-stu-id="c7e45-108">This challenge can be handled using Docker clustering software or an orchestrator.</span></span> <span data-ttu-id="c7e45-109">Když prozkoumáme přístupy k mikroslužbám, podíváme se na orchestraci podrobněji v další části.</span><span class="sxs-lookup"><span data-stu-id="c7e45-109">We'll look at orchestrators in greater detail in the next section, when we explore microservices approaches.</span></span>

<span data-ttu-id="c7e45-110">Kontejnery Docker jsou užitečné (ale nevyžadují se) pro tradiční architektury zaměřené na služby a pokročilejší architektury mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="c7e45-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="c7e45-111">Na konci dne jsou řešení clusteringu kontejneru užitečná pro tradiční architekturu SOA i pro pokročilejší architekturu mikroslužeb, ve které každá mikroslužba vlastní svůj datový model.</span><span class="sxs-lookup"><span data-stu-id="c7e45-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture and for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="c7e45-112">A díky více databázím můžete také škálovat datovou vrstvu místo práce s monolitické databázemi sdílenými službami SOA.</span><span class="sxs-lookup"><span data-stu-id="c7e45-112">And thanks to multiple databases, you also can scale out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="c7e45-113">Diskuze o rozdělení dat je ale čistě o architektuře a návrhu.</span><span class="sxs-lookup"><span data-stu-id="c7e45-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c7e45-114">[Předchozí](state-and-data-in-docker-applications.md)Další
>[](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="c7e45-114">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>
