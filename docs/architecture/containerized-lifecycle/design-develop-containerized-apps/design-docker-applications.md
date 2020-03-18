---
title: Návrh aplikací Dockeru
description: Zde naleznete odkaz na podrobný průvodce architekturou mikroslužeb, protože to je téma, které není podrobně popsáno v této příručce.
ms.date: 02/15/2019
ms.openlocfilehash: b9539ff4edf405ab890d83be59a248ffa2360c99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295863"
---
# <a name="design-docker-applications"></a><span data-ttu-id="82d21-103">Návrh aplikací Dockeru</span><span class="sxs-lookup"><span data-stu-id="82d21-103">Design Docker applications</span></span>

<span data-ttu-id="82d21-104">Kapitola 1 představila základní koncepty týkající se kontejnerů a Dockeru.</span><span class="sxs-lookup"><span data-stu-id="82d21-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="82d21-105">Tyto informace jsou základní úrovní informací, které potřebujete k zahájení.</span><span class="sxs-lookup"><span data-stu-id="82d21-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="82d21-106">Podnikové aplikace však mohou být složité a složené z více služeb namísto jedné služby nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="82d21-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="82d21-107">Pro tyto volitelné případy použití, musíte znát další přístupy k návrhu, jako je například architektura orientovaná na služby (SOA) a pokročilejší koncepty mikroslužeb a koncepty orchestrace kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="82d21-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="82d21-108">Rozsah tohoto dokumentu není omezena na mikroslužeb, ale na všechny dockerové aplikace životního cyklu, proto není prozkoumat architekturu mikroslužeb do hloubky, protože můžete také použít kontejnery a Docker s pravidelným SOA, úlohy na pozadí nebo úlohy, nebo dokonce s monolitickými přístupy k nasazení aplikací.</span><span class="sxs-lookup"><span data-stu-id="82d21-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="82d21-109">**Více informací** Další informace o podnikových aplikacích a architektuře mikroslužeb do hloubky naleznete v průvodci NET <https://aka.ms/MicroservicesEbook> [Microservices: Architecture for Containerized .NET Applications,](../../microservices/index.md) které můžete také stáhnout z aplikace .</span><span class="sxs-lookup"><span data-stu-id="82d21-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="82d21-110">Než se však dostaneme do životního cyklu aplikace a devops, je důležité vědět, jak budete navrhovat a konstruovat aplikaci a jaké jsou vaše možnosti návrhu.</span><span class="sxs-lookup"><span data-stu-id="82d21-110">However, before we get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="82d21-111">[Předchozí](index.md)
>[další](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="82d21-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
