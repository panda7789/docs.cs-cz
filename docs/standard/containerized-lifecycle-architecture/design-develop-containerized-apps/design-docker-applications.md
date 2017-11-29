---
title: "Návrh aplikace Docker"
description: "Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: db8376abf95aab51fad23f4b351cb772351117ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="design-docker-applications"></a><span data-ttu-id="f912e-104">Návrh aplikace Docker</span><span class="sxs-lookup"><span data-stu-id="f912e-104">Design Docker applications</span></span>

<span data-ttu-id="f912e-105">Kapitola 1 zavedly základní koncepty týkající se kontejnery a Docker.</span><span class="sxs-lookup"><span data-stu-id="f912e-105">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="f912e-106">Tyto informace je základní úroveň informace, které potřebujete, abyste mohli začít.</span><span class="sxs-lookup"><span data-stu-id="f912e-106">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="f912e-107">Ale podnikové aplikace, které může být složité a skládat z několika služeb místo jednu službu nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="f912e-107">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="f912e-108">Pro případy nepovinným použitím musíte znát další přístupy k návrhu, jako je architektura Service-Oriented (SOA) a pokročilejší mikroslužeb koncepty a kontejner koncepty orchestration.</span><span class="sxs-lookup"><span data-stu-id="f912e-108">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="f912e-109">Rámec tohoto dokumentu se neomezuje na mikroslužeb, ale žádné Docker aplikace životní cyklus, proto ji není prozkoumat mikroslužeb architektura podrobněji, protože také můžete použít kontejnery a Docker pomocí regulárních SAO, úlohy na pozadí nebo úlohy, nebo dokonce i s přístupy k nasazení monolitický aplikace.</span><span class="sxs-lookup"><span data-stu-id="f912e-109">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SAO, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="f912e-110">Ale předtím, než se nám získat do životního cyklu aplikace a DevOps, je důležité vědět, jak se chystáte návrhu a vytvořit aplikace a jaké jsou vaše volby návrhu.</span><span class="sxs-lookup"><span data-stu-id="f912e-110">However, before we get into the application life cycle and DevOps, it is important to know how you are going to design and construct your application and what are your design choices.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="f912e-111">[Předchozí] (index.md) [Další] (běžné kontejneru návrhu principles.md)</span><span class="sxs-lookup"><span data-stu-id="f912e-111">[Previous] (index.md) [Next] (common-container-design-principles.md)</span></span>
