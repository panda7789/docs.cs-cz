---
title: Návrh aplikací Dockeru
description: Tady najít odkaz na podrobné příručce k architektuře mikroslužeb, protože se na téma, který není podrobně popsané v této příručce.
ms.date: 02/15/2019
ms.openlocfilehash: 535b6cefb7371014527032972ec27ebfe4b67ebc
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644679"
---
# <a name="design-docker-applications"></a><span data-ttu-id="68e84-103">Návrh aplikací Dockeru</span><span class="sxs-lookup"><span data-stu-id="68e84-103">Design Docker applications</span></span>

<span data-ttu-id="68e84-104">Kapitoly 1 jsme zavedli základní koncepty týkající se kontejnerů a Dockeru.</span><span class="sxs-lookup"><span data-stu-id="68e84-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="68e84-105">Tyto informace je základní úroveň informací, které potřebujete, abyste mohli začít.</span><span class="sxs-lookup"><span data-stu-id="68e84-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="68e84-106">Ale podnikových aplikací mohou být složité a skládá z několika služeb namísto jedné služby nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="68e84-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="68e84-107">Pro tyto případy použití volitelné je potřeba vědět další přístupy k návrhu, jako je architektura Service-Oriented (SOA) a pokročilejší koncepty mikroslužeb a kontejnerů koncepty Orchestrace.</span><span class="sxs-lookup"><span data-stu-id="68e84-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="68e84-108">Rámec tohoto dokumentu se neomezuje na mikroslužby ale do jakékoli Docker aplikace životního cyklu, proto ho není prozkoumat architektury mikroslužeb do hloubky protože také můžete použít kontejnerům a Dockeru s regulární SOA, úlohy na pozadí nebo úlohy, nebo dokonce i s monolitickými aplikacemi způsoby nasazení.</span><span class="sxs-lookup"><span data-stu-id="68e84-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="68e84-109">**Další informace o** Další informace o podnikové aplikace a architekturu mikroslužeb do hloubky, přečtěte si příručku [NET Mikroslužeb: Architektura pro Kontejnerizovaných aplikací .NET](../../microservices-architecture/index.md) , který si můžete stáhnout také z <https://aka.ms/MicroservicesEbook>.</span><span class="sxs-lookup"><span data-stu-id="68e84-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices-architecture/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="68e84-110">Ale předtím, než se dostaneme k životního cyklu aplikace a DevOps, je důležité vědět, jak budete k návrhu a sestavování vaší aplikace a jaké jsou vaše volby při návrhu.</span><span class="sxs-lookup"><span data-stu-id="68e84-110">However, before we get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="68e84-111">[Předchozí](index.md)
>[další](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="68e84-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
