---
title: Aplikace .NET založené na návrh a vývoj více kontejnerech a Mikroslužbách
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Vysvětlení externí architektury pro návrh a vývoj více kontejnerech a aplikacích .NET na základě Mikroslužeb.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 3bbf746aa9c0b66a097b8c4df2964b5679342fd0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973625"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a><span data-ttu-id="44194-103">Návrh a vývoj aplikací .NET více kontejnerů a založených na Mikroslužbách</span><span class="sxs-lookup"><span data-stu-id="44194-103">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>

<span data-ttu-id="44194-104">*Vývoj aplikací pro kontejnerizované mikroslužby znamená, že vytváříte vícekontejnerových aplikací. Ale může také být jednodušší vícekontejnerová aplikace – například třívrstvé aplikace – a nemusí být sestaveno pomocí architekturu mikroslužeb.*</span><span class="sxs-lookup"><span data-stu-id="44194-104">*Developing containerized microservice applications means you are building multi-container applications. However, a multi-container application could also be simpler—for example, a three-tier application—and might not be built using a microservice architecture.*</span></span>

<span data-ttu-id="44194-105">Dříve jsme vyvolána na otázku "Je Docker nezbytné při vytváření architektury mikroslužeb?"</span><span class="sxs-lookup"><span data-stu-id="44194-105">Earlier we raised the question "Is Docker necessary when building a microservice architecture?"</span></span> <span data-ttu-id="44194-106">Odpověď je vymazat č.</span><span class="sxs-lookup"><span data-stu-id="44194-106">The answer is a clear no.</span></span> <span data-ttu-id="44194-107">Docker je podpůrnou technologii a může poskytnout významné výhody, ale kontejnerů a Dockeru nejsou o striktní požadavek pro mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="44194-107">Docker is an enabler and can provide significant benefits, but containers and Docker are not a hard requirement for microservices.</span></span> <span data-ttu-id="44194-108">Například můžete vytvořit aplikace založená na mikroslužbách s nebo bez něj Docker při použití Azure Service Fabric, která podporuje mikroslužeb spouštěných jako jednoduchý proces, nebo jako kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="44194-108">As an example, you could create a microservices-based application with or without Docker when using Azure Service Fabric, which supports microservices running as simple processes or as Docker containers.</span></span>

<span data-ttu-id="44194-109">Ale pokud víte, jak pro návrh a vývoj aplikací založených na mikroslužbách, také založené na kontejnerech Dockeru, vám bude moct navrhovat a vyvíjet jiné aplikační model jednodušší.</span><span class="sxs-lookup"><span data-stu-id="44194-109">However, if you know how to design and develop a microservices-based application that is also based on Docker containers, you will be able to design and develop any other, simpler application model.</span></span> <span data-ttu-id="44194-110">Například můžete navrhnout třívrstvé aplikace, který taky vyžaduje přístup více kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="44194-110">For example, you might design a three-tier application that also requires a multi-container approach.</span></span> <span data-ttu-id="44194-111">Z důvodu, a protože architektury mikroslužeb jsou důležité trend v rámci světa kontejneru, tato část se zaměřuje na implementaci architektury mikroslužeb pomocí kontejnerů Dockeru.</span><span class="sxs-lookup"><span data-stu-id="44194-111">Because of that, and because microservice architectures are an important trend within the container world, this section focuses on a microservice architecture implementation using Docker containers.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="44194-112">[Předchozí](../docker-application-development-process/docker-app-development-workflow.md)
>[další](microservice-application-design.md)</span><span class="sxs-lookup"><span data-stu-id="44194-112">[Previous](../docker-application-development-process/docker-app-development-workflow.md)
[Next](microservice-application-design.md)</span></span>