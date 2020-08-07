---
title: Návrh aplikací Dockeru
description: Tady najdete odkaz na podrobný Průvodce architekturou mikroslužeb, protože to je téma, které v této příručce není popsané.
ms.date: 08/06/2020
ms.openlocfilehash: b63d4344abb358a393587bdacf91f6091b531af0
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915972"
---
# <a name="design-docker-applications"></a><span data-ttu-id="57d3b-103">Návrh aplikací Dockeru</span><span class="sxs-lookup"><span data-stu-id="57d3b-103">Design Docker applications</span></span>

<span data-ttu-id="57d3b-104">Kapitola 1 představila základní koncepty týkající se kontejnerů a Docker.</span><span class="sxs-lookup"><span data-stu-id="57d3b-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="57d3b-105">Tyto informace jsou základními informacemi, které potřebujete, abyste mohli začít.</span><span class="sxs-lookup"><span data-stu-id="57d3b-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="57d3b-106">Podnikové aplikace ale můžou být složité a skládají se z několika služeb místo jediné služby nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="57d3b-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="57d3b-107">Pro tyto volitelné případy použití potřebujete znát další postupy pro návrh, jako je například architektura orientované na služby (SOA) a pokročilejší koncepty mikroslužeb a koncepty orchestrace kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="57d3b-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="57d3b-108">Rozsah tohoto dokumentu není omezený na mikroslužby, ale i na jakýkoli životní cyklus aplikace Docker, proto nezkoumá architekturu mikroslužeb v hloubkě, protože můžete také použít kontejnery a Docker s pravidelným záznamem SOA, úlohami na pozadí nebo úlohami nebo dokonce s přístupy k nasazení aplikací monolitické.</span><span class="sxs-lookup"><span data-stu-id="57d3b-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you can also use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="57d3b-109">**Další informace** Pokud chcete získat další informace o architektuře podnikových aplikací a mikroslužeb, přečtěte si příručku [net mikroslužby: architektura pro kontejnerové aplikace .NET](../../microservices/index.md) , ze kterých si můžete také stáhnout <https://aka.ms/MicroservicesEbook> .</span><span class="sxs-lookup"><span data-stu-id="57d3b-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="57d3b-110">Před tím, než se dostanete k životnímu cyklu aplikace a DevOps, je důležité, abyste věděli, jak navrhnout a sestavit aplikaci a jaké jsou vaše možnosti návrhu.</span><span class="sxs-lookup"><span data-stu-id="57d3b-110">However, before you get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="57d3b-111">[Předchozí](index.md) 
> [Další](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="57d3b-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
