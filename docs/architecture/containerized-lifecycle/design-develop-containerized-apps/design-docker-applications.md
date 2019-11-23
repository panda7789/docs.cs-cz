---
title: Návrh aplikací Dockeru
description: Tady najdete odkaz na podrobný Průvodce architekturou mikroslužeb, protože to je téma, které v této příručce není popsané.
ms.date: 02/15/2019
ms.openlocfilehash: b9539ff4edf405ab890d83be59a248ffa2360c99
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295863"
---
# <a name="design-docker-applications"></a><span data-ttu-id="555ee-103">Návrh aplikací Dockeru</span><span class="sxs-lookup"><span data-stu-id="555ee-103">Design Docker applications</span></span>

<span data-ttu-id="555ee-104">Kapitola 1 představila základní koncepty týkající se kontejnerů a Docker.</span><span class="sxs-lookup"><span data-stu-id="555ee-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="555ee-105">Tyto informace jsou základními informacemi, které potřebujete, abyste mohli začít.</span><span class="sxs-lookup"><span data-stu-id="555ee-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="555ee-106">Podnikové aplikace ale můžou být složité a skládají se z několika služeb místo jediné služby nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="555ee-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="555ee-107">Pro tyto volitelné případy použití potřebujete znát další postupy pro návrh, jako je například architektura orientované na služby (SOA) a pokročilejší koncepty mikroslužeb a koncepty orchestrace kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="555ee-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="555ee-108">Rozsah tohoto dokumentu není omezený na mikroslužby, ale i na jakýkoli životní cyklus aplikace Docker, proto nezkoumá architekturu mikroslužeb v hloubkě, protože můžete také použít kontejnery a Docker s pravidelným záznamem SOA, úlohami na pozadí nebo úlohami i s přístupy k nasazení aplikací monolitické.</span><span class="sxs-lookup"><span data-stu-id="555ee-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="555ee-109">**Další informace** Pokud chcete získat další informace o architektuře podnikových aplikací a mikroslužeb, přečtěte si příručku [net mikroslužby: architektura pro kontejnerové aplikace .NET](../../microservices/index.md) , které můžete také stáhnout z <https://aka.ms/MicroservicesEbook>.</span><span class="sxs-lookup"><span data-stu-id="555ee-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="555ee-110">Před tím, než se dostanete k životnímu cyklu aplikace a DevOps, je důležité znát způsob návrhu a sestavování aplikace a možností vašich návrhů.</span><span class="sxs-lookup"><span data-stu-id="555ee-110">However, before we get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="555ee-111">[Předchozí](index.md)
>[Další](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="555ee-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
