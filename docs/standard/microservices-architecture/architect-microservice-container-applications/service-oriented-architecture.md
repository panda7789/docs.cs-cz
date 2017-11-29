---
title: "Architektura orientovaná na služby"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Architektura orientovaná na služby"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 970ff86c77100077d4c7710c0a697d1745d35819
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="service-oriented-architecture"></a><span data-ttu-id="996da-104">Architektura orientovaná na služby</span><span class="sxs-lookup"><span data-stu-id="996da-104">Service-oriented architecture</span></span> 

<span data-ttu-id="996da-105">Architektura orientovaná na služby (SOA) byl Nepromyšlené termín a je určena různých věcí na jiné osoby.</span><span class="sxs-lookup"><span data-stu-id="996da-105">Service-oriented architecture (SOA) was an overused term and has meant different things to different people.</span></span> <span data-ttu-id="996da-106">Ale jako společný jmenovatel, SOA znamená, že struktury vaší aplikace pomocí decomposing k více službám (nejčastěji jako služeb HTTP), které můžou být klasifikované jako různé typy jako subsystémy nebo vrstvy.</span><span class="sxs-lookup"><span data-stu-id="996da-106">But as a common denominator, SOA means that you structure your application by decomposing it into multiple services (most commonly as HTTP services) that can be classified as different types like subsystems or tiers.</span></span>

<span data-ttu-id="996da-107">Tyto služby teď můžou být nasazené jako Docker kontejnery, které řeší problémy při nasazení, protože všechny závislosti jsou součástí image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="996da-107">Those services can now be deployed as Docker containers, which solves deployment issues, because all the dependencies are included in the container image.</span></span> <span data-ttu-id="996da-108">Pokud potřebujete škálování aplikace SOA, můžete mít škálovatelnost a dostupnost výzvy, pokud nasazujete podle jednoho hostitelů Docker.</span><span class="sxs-lookup"><span data-stu-id="996da-108">However, when you need to scale up SOA applications, you might have scalability and availability challenges if you are deploying based on single Docker hosts.</span></span> <span data-ttu-id="996da-109">Toto je, kde Docker clustering softwaru nebo orchestrator vám pomůže se, jak je popsáno v pozdějších částech, kde jsme popisují nasazení přístupy k mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="996da-109">This is where Docker clustering software or an orchestrator will help you out, as explained in later sections where we describe deployment approaches for microservices.</span></span>

<span data-ttu-id="996da-110">Kontejnery docker jsou užitečné (ale není požadováno) pro tradiční architektury orientované na služby a pokročilejší architektury mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="996da-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="996da-111">Mikroslužeb odvozena od SOA, ale SOA se liší od architektura mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="996da-111">Microservices derive from SOA, but SOA is different from microservices architecture.</span></span> <span data-ttu-id="996da-112">Funkce, například velký centrální zprostředkovatelé, centrální orchestrators na úrovni organizace a [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) jsou typická ve SOA.</span><span class="sxs-lookup"><span data-stu-id="996da-112">Features like big central brokers, central orchestrators at the organization level, and the [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) are typical in SOA.</span></span> <span data-ttu-id="996da-113">Ale ve většině případů se jedná o proti vzory v komunitě mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="996da-113">But in most cases, these are anti-patterns in the microservice community.</span></span> <span data-ttu-id="996da-114">Ve skutečnosti někteří uživatelé uvádějí, že "architektury mikroslužby je SOA pracujete správně."</span><span class="sxs-lookup"><span data-stu-id="996da-114">In fact, some people argue that “The microservice architecture is SOA done right.”</span></span>

<span data-ttu-id="996da-115">Tato příručka se zaměřuje na mikroslužeb, protože je doporučený méně než požadavky a postupy používané při architektury mikroslužby SOA přístup.</span><span class="sxs-lookup"><span data-stu-id="996da-115">This guide focuses on microservices, because a SOA approach is less prescriptive than the requirements and techniques used in a microservice architecture.</span></span> <span data-ttu-id="996da-116">Pokud víte, jak sestavit aplikaci na základě mikroslužbu, také znát postup sestavení jednodušší aplikace orientované na služby.</span><span class="sxs-lookup"><span data-stu-id="996da-116">If you know how to build a microservice-based application, you also know how to build a simpler service-oriented application.</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="996da-117">[Předchozí] (docker aplikace stavu data.md) [Další] (mikroslužeb architecture.md)</span><span class="sxs-lookup"><span data-stu-id="996da-117">[Previous] (docker-application-state-data.md) [Next] (microservices-architecture.md)</span></span>
