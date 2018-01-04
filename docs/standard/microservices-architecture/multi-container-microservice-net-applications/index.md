---
title: "Návrh a vývoj Mikroslužbu a více kontejneru na základě aplikací .NET"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Návrh a vývoj Mikroslužbu a více kontejneru na základě aplikací .NET"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2a4c59c63cb3f76975173663948e94a7c64ef193
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a><span data-ttu-id="3a520-104">Návrh a vývoj aplikace s více kontejneru a na základě Mikroslužbu .NET</span><span class="sxs-lookup"><span data-stu-id="3a520-104">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>

<span data-ttu-id="3a520-105">*Vývoj aplikací kontejnerizované mikroslužbu znamená, že vytváříte více kontejneru aplikace. Ale aplikace s více kontejnerů mohou být také jednodušší – například třívrstvá aplikace – a nemusí být vytvořená s využitím architektury mikroslužby.*</span><span class="sxs-lookup"><span data-stu-id="3a520-105">*Developing containerized microservice applications means you are building multi-container applications. However, a multi-container application could also be simpler—for example, a three-tier application—and might not be built using a microservice architecture.*</span></span>

<span data-ttu-id="3a520-106">Dříve jsme vyvolá na otázku "Je Docker potřebné při sestavování architektury mikroslužby?"</span><span class="sxs-lookup"><span data-stu-id="3a520-106">Earlier we raised the question “Is Docker necessary when building a microservice architecture?”</span></span> <span data-ttu-id="3a520-107">Odpověď je zrušte ne.</span><span class="sxs-lookup"><span data-stu-id="3a520-107">The answer is a clear no.</span></span> <span data-ttu-id="3a520-108">Docker je podpůrnou technologii a může poskytnout významné výhody, ale kontejnery a Docker nejsou pevný požadavek pro mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="3a520-108">Docker is an enabler and can provide significant benefits, but containers and Docker are not a hard requirement for microservices.</span></span> <span data-ttu-id="3a520-109">Jako příklad může vytvořte aplikaci na základě mikroslužeb s nebo bez Docker při použití Azure Service Fabric, která podporuje běží jako jednoduchý procesy nebo jako kontejnery Docker mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="3a520-109">As an example, you could create a microservices-based application with or without Docker when using Azure Service Fabric, which supports microservices running as simple processes or as Docker containers.</span></span>

<span data-ttu-id="3a520-110">Ale pokud víte, jak pro návrh a vývoj aplikace na základě mikroslužeb také založené na Docker kontejnery, bude moct návrh a vývoj jiných, aplikační model jednodušší.</span><span class="sxs-lookup"><span data-stu-id="3a520-110">However, if you know how to design and develop a microservices-based application that is also based on Docker containers, you will be able to design and develop any other, simpler application model.</span></span> <span data-ttu-id="3a520-111">Například můžete navrhnout třívrstvá aplikace, který taky vyžaduje přístup více kontejneru.</span><span class="sxs-lookup"><span data-stu-id="3a520-111">For example, you might design a three-tier application that also requires a multi-container approach.</span></span> <span data-ttu-id="3a520-112">Z tohoto důvodu a protože architektury mikroslužby jsou důležité trend v rámci světa kontejneru, tato část se zaměřuje na na implementace architektury mikroslužby pomocí Docker kontejnery.</span><span class="sxs-lookup"><span data-stu-id="3a520-112">Because of that, and because microservice architectures are an important trend within the container world, this section focuses on a microservice architecture implementation using Docker containers.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="3a520-113">[Předchozí] (.. /containerize-NET-Framework-Applications/index.MD) [Další] (mikroslužbu design.md aplikace)</span><span class="sxs-lookup"><span data-stu-id="3a520-113">[Previous] (../containerize-net-framework-applications/index.md) [Next] (microservice-application-design.md)</span></span>
