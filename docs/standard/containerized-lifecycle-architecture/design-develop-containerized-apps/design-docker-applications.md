---
title: Návrh aplikací Dockeru
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: d02cec0595024eb7bd7c0ac46df093359680da74
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155376"
---
# <a name="design-docker-applications"></a><span data-ttu-id="af354-103">Návrh aplikací Dockeru</span><span class="sxs-lookup"><span data-stu-id="af354-103">Design Docker applications</span></span>

<span data-ttu-id="af354-104">Kapitoly 1 jsme zavedli základní koncepty týkající se kontejnerů a Dockeru.</span><span class="sxs-lookup"><span data-stu-id="af354-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="af354-105">Tyto informace je základní úroveň informací, které potřebujete, abyste mohli začít.</span><span class="sxs-lookup"><span data-stu-id="af354-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="af354-106">Ale podnikových aplikací mohou být složité a skládá z několika služeb namísto jedné služby nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="af354-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="af354-107">Pro tyto případy použití volitelné je potřeba vědět další přístupy k návrhu, jako je architektura Service-Oriented (SOA) a pokročilejší koncepty mikroslužeb a kontejnerů koncepty Orchestrace.</span><span class="sxs-lookup"><span data-stu-id="af354-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="af354-108">Rámec tohoto dokumentu se neomezuje na mikroslužby ale do jakékoli Docker aplikace životního cyklu, proto ho není prozkoumat architektury mikroslužeb do hloubky protože také můžete použít kontejnerům a Dockeru s regulární SAO, úlohy na pozadí nebo úlohy, nebo dokonce i s monolitickými aplikacemi způsoby nasazení.</span><span class="sxs-lookup"><span data-stu-id="af354-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SAO, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="af354-109">Ale předtím, než se dostaneme k životního cyklu aplikace a DevOps, je důležité vědět, jak chcete navrhnout a sestavit aplikaci a jaké jsou vaše volby při návrhu.</span><span class="sxs-lookup"><span data-stu-id="af354-109">However, before we get into the application life cycle and DevOps, it is important to know how you are going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="af354-110">[Předchozí](index.md)
>[další](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="af354-110">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>