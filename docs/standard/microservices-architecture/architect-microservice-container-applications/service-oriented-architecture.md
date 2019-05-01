---
title: Architektura orientovaná na služby
description: Přečtěte si základní rozdíly mezi mikroslužbami a architektura orientovaná na služby (SOA).
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: d19053d8296dbe75ac1e0ce037d6a713d9f5687c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62025480"
---
# <a name="service-oriented-architecture"></a><span data-ttu-id="f6e96-103">Architektura orientovaná na služby</span><span class="sxs-lookup"><span data-stu-id="f6e96-103">Service-oriented architecture</span></span>

<span data-ttu-id="f6e96-104">Architektura orientovaná na služby (SOA) byl Nepromyšlené období a má určené různé věci pro různé osoby.</span><span class="sxs-lookup"><span data-stu-id="f6e96-104">Service-oriented architecture (SOA) was an overused term and has meant different things to different people.</span></span> <span data-ttu-id="f6e96-105">Ale jako společným faktorem SOA znamená, že struktury aplikace pomocí rozložení do více služeb (nejčastěji jako služeb HTTP), které se dají považovat za různé typy jako podsystémy nebo úrovní.</span><span class="sxs-lookup"><span data-stu-id="f6e96-105">But as a common denominator, SOA means that you structure your application by decomposing it into multiple services (most commonly as HTTP services) that can be classified as different types like subsystems or tiers.</span></span>

<span data-ttu-id="f6e96-106">Tyto služby můžete nasadit jako kontejnery Dockeru, které řeší problémy s nasazením, protože všechny závislosti jsou součástí image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="f6e96-106">Those services can now be deployed as Docker containers, which solves deployment issues, because all the dependencies are included in the container image.</span></span> <span data-ttu-id="f6e96-107">Pokud potřebujete vertikálně navýšit kapacitu aplikace SOA, bude pravděpodobně škálovatelnost a dostupnost výzvy, pokud nasazujete založené na jednoho hostitele Dockeru.</span><span class="sxs-lookup"><span data-stu-id="f6e96-107">However, when you need to scale up SOA applications, you might have scalability and availability challenges if you're deploying based on single Docker hosts.</span></span> <span data-ttu-id="f6e96-108">To je, kde software clusteru Docker nebo orchestrátor vám umožňují, jak je popsáno v předchozích částech, kde jsou popsány přístupy k nasazení mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="f6e96-108">This is where Docker clustering software or an orchestrator can help you, as explained in later sections where deployment approaches for microservices are described.</span></span>

<span data-ttu-id="f6e96-109">Kontejnery dockeru jsou užitečné (ale nevyžadováno) pro tradiční architektury orientované na služby a pokročilejší architekturu mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="f6e96-109">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="f6e96-110">Mikroslužby jsou odvozeny z SOA, ale SOA se liší od architekturu mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="f6e96-110">Microservices derive from SOA, but SOA is different from microservices architecture.</span></span> <span data-ttu-id="f6e96-111">Funkce, jako jsou velké centrální zprostředkovatelů, centrální orchestrátorů na úrovni organizace a [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) jsou běžná v SOA.</span><span class="sxs-lookup"><span data-stu-id="f6e96-111">Features like large central brokers, central orchestrators at the organization level, and the [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) are typical in SOA.</span></span> <span data-ttu-id="f6e96-112">Ale ve většině případů Toto jsou antimodely v komunitě mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="f6e96-112">But in most cases, these are anti-patterns in the microservice community.</span></span> <span data-ttu-id="f6e96-113">Ve skutečnosti někteří lidé tvrdí, že "architekturu mikroslužeb je SOA pracujete správně."</span><span class="sxs-lookup"><span data-stu-id="f6e96-113">In fact, some people argue that "The microservice architecture is SOA done right."</span></span>

<span data-ttu-id="f6e96-114">Tato příručka se zaměřuje na mikroslužby, protože SOA přístup je méně než požadavky a postupy používané v architektuře mikroslužeb doporučené postupy.</span><span class="sxs-lookup"><span data-stu-id="f6e96-114">This guide focuses on microservices, because a SOA approach is less prescriptive than the requirements and techniques used in a microservice architecture.</span></span> <span data-ttu-id="f6e96-115">Pokud víte, jak vytvářet aplikace založené na mikroslužbách, také víte, jak vytvářet aplikace orientované na služby jednodušší.</span><span class="sxs-lookup"><span data-stu-id="f6e96-115">If you know how to build a microservice-based application, you also know how to build a simpler service-oriented application.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f6e96-116">[Předchozí](docker-application-state-data.md)
>[další](microservices-architecture.md)</span><span class="sxs-lookup"><span data-stu-id="f6e96-116">[Previous](docker-application-state-data.md)
[Next](microservices-architecture.md)</span></span>