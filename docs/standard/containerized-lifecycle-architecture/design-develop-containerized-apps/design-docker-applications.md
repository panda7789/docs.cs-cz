---
title: Návrh aplikace Docker
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 6525e5f80ebb0551e4f85904a467d862aa4133ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567728"
---
# <a name="design-docker-applications"></a><span data-ttu-id="42f5f-103">Návrh aplikace Docker</span><span class="sxs-lookup"><span data-stu-id="42f5f-103">Design Docker applications</span></span>

<span data-ttu-id="42f5f-104">Kapitola 1 zavedly základní koncepty týkající se kontejnery a Docker.</span><span class="sxs-lookup"><span data-stu-id="42f5f-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="42f5f-105">Tyto informace je základní úroveň informace, které potřebujete, abyste mohli začít.</span><span class="sxs-lookup"><span data-stu-id="42f5f-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="42f5f-106">Ale podnikové aplikace, které může být složité a skládat z několika služeb místo jednu službu nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="42f5f-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="42f5f-107">Pro případy nepovinným použitím musíte znát další přístupy k návrhu, jako je architektura Service-Oriented (SOA) a pokročilejší mikroslužeb koncepty a kontejner koncepty orchestration.</span><span class="sxs-lookup"><span data-stu-id="42f5f-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="42f5f-108">Rámec tohoto dokumentu se neomezuje na mikroslužeb, ale žádné Docker aplikace životní cyklus, proto ji není prozkoumat mikroslužeb architektura podrobněji, protože také můžete použít kontejnery a Docker pomocí regulárních SAO, úlohy na pozadí nebo úlohy, nebo dokonce i s přístupy k nasazení monolitický aplikace.</span><span class="sxs-lookup"><span data-stu-id="42f5f-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SAO, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="42f5f-109">Ale předtím, než se nám získat do životního cyklu aplikace a DevOps, je důležité vědět, jak se chystáte návrhu a vytvořit aplikace a jaké jsou vaše volby návrhu.</span><span class="sxs-lookup"><span data-stu-id="42f5f-109">However, before we get into the application life cycle and DevOps, it is important to know how you are going to design and construct your application and what are your design choices.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="42f5f-110">[Předchozí] (index.md) [Další] (běžné kontejneru návrhu principles.md)</span><span class="sxs-lookup"><span data-stu-id="42f5f-110">[Previous] (index.md) [Next] (common-container-design-principles.md)</span></span>
