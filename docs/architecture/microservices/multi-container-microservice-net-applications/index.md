---
title: Navrhování a vývoj aplikací .NET založených na více kontejnerech a mikroslužbách
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Seznamte se s externí architekturou pro navrhování a vývoj aplikací .NET založených na více kontejnerech a mikroslužbách.
ms.date: 10/02/2018
ms.openlocfilehash: 8c2f828e9913a0efcdf580371124b0f624daeffe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "70296624"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a><span data-ttu-id="8af19-103">Navrhování a vývoj vícekontejnerových a mikroslužeb založených na aplikacích .NET</span><span class="sxs-lookup"><span data-stu-id="8af19-103">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>

<span data-ttu-id="8af19-104">*Vývoj kontejnerizovaných aplikací mikroslužeb znamená, že vytváříte aplikace s více kontejnery. Aplikace s více kontejnery však může být také jednodušší – například třívrstvá aplikace – a nemusí být sestavena pomocí architektury mikroslužeb.*</span><span class="sxs-lookup"><span data-stu-id="8af19-104">*Developing containerized microservice applications means you are building multi-container applications. However, a multi-container application could also be simpler—for example, a three-tier application—and might not be built using a microservice architecture.*</span></span>

<span data-ttu-id="8af19-105">Dříve jsme vznesli otázku "Je Docker nutné při vytváření architektury mikroslužeb?"</span><span class="sxs-lookup"><span data-stu-id="8af19-105">Earlier we raised the question "Is Docker necessary when building a microservice architecture?"</span></span> <span data-ttu-id="8af19-106">Odpověď je jasné ne.</span><span class="sxs-lookup"><span data-stu-id="8af19-106">The answer is a clear no.</span></span> <span data-ttu-id="8af19-107">Docker je enabler a může poskytnout významné výhody, ale kontejnery a Docker nejsou pevný požadavek pro mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="8af19-107">Docker is an enabler and can provide significant benefits, but containers and Docker are not a hard requirement for microservices.</span></span> <span data-ttu-id="8af19-108">Jako příklad můžete vytvořit aplikaci založenou na mikroslužbách s Nebo bez Dockeru při použití Azure Service Fabric, který podporuje mikroslužby spuštěné jako jednoduché procesy nebo jako kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="8af19-108">As an example, you could create a microservices-based application with or without Docker when using Azure Service Fabric, which supports microservices running as simple processes or as Docker containers.</span></span>

<span data-ttu-id="8af19-109">Pokud však víte, jak navrhnout a vyvinout aplikaci založenou na mikroslužbách, která je také založena na kontejnerech Dockeru, budete moci navrhovat a vyvíjet jakýkoli jiný, jednodušší aplikační model.</span><span class="sxs-lookup"><span data-stu-id="8af19-109">However, if you know how to design and develop a microservices-based application that is also based on Docker containers, you will be able to design and develop any other, simpler application model.</span></span> <span data-ttu-id="8af19-110">Můžete například navrhnout třívrstvou aplikaci, která také vyžaduje přístup s více kontejnery.</span><span class="sxs-lookup"><span data-stu-id="8af19-110">For example, you might design a three-tier application that also requires a multi-container approach.</span></span> <span data-ttu-id="8af19-111">Z tohoto důvodu a protože architektury mikroslužeb jsou důležitým trendem ve světě kontejnerů, tato část se zaměřuje na implementaci architektury mikroslužeb pomocí kontejnerů Dockeru.</span><span class="sxs-lookup"><span data-stu-id="8af19-111">Because of that, and because microservice architectures are an important trend within the container world, this section focuses on a microservice architecture implementation using Docker containers.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8af19-112">[Předchozí](../docker-application-development-process/docker-app-development-workflow.md)
>[další](microservice-application-design.md)</span><span class="sxs-lookup"><span data-stu-id="8af19-112">[Previous](../docker-application-development-process/docker-app-development-workflow.md)
[Next](microservice-application-design.md)</span></span>
