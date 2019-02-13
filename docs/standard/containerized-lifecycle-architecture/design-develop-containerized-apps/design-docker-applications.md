---
title: Návrh aplikací Dockeru
description: Tady najít odkaz na podrobné příručce k architektuře mikroslužeb, protože se na téma, který není podrobně popsané v této příručce.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: f31421cab7d2072441999231adfbe771a3f9a0f5
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220202"
---
# <a name="design-docker-applications"></a><span data-ttu-id="38111-103">Návrh aplikací Dockeru</span><span class="sxs-lookup"><span data-stu-id="38111-103">Design Docker applications</span></span>

<span data-ttu-id="38111-104">Kapitoly 1 jsme zavedli základní koncepty týkající se kontejnerů a Dockeru.</span><span class="sxs-lookup"><span data-stu-id="38111-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="38111-105">Tyto informace je základní úroveň informací, které potřebujete, abyste mohli začít.</span><span class="sxs-lookup"><span data-stu-id="38111-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="38111-106">Ale podnikových aplikací mohou být složité a skládá z několika služeb namísto jedné služby nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="38111-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="38111-107">Pro tyto případy použití volitelné je potřeba vědět další přístupy k návrhu, jako je architektura Service-Oriented (SOA) a pokročilejší koncepty mikroslužeb a kontejnerů koncepty Orchestrace.</span><span class="sxs-lookup"><span data-stu-id="38111-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="38111-108">Rámec tohoto dokumentu se neomezuje na mikroslužby ale do jakékoli Docker aplikace životního cyklu, proto ho není prozkoumat architektury mikroslužeb do hloubky protože také můžete použít kontejnerům a Dockeru s regulární SAO, úlohy na pozadí nebo úlohy, nebo dokonce i s monolitickými aplikacemi způsoby nasazení.</span><span class="sxs-lookup"><span data-stu-id="38111-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SAO, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="38111-109">Ale předtím, než se dostaneme k životního cyklu aplikace a DevOps, je důležité vědět, jak chcete navrhnout a sestavit aplikaci a jaké jsou vaše volby při návrhu.</span><span class="sxs-lookup"><span data-stu-id="38111-109">However, before we get into the application life cycle and DevOps, it is important to know how you are going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="38111-110">[Předchozí](index.md)
>[další](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="38111-110">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>