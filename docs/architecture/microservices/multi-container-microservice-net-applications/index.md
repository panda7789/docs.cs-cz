---
title: Navrhování a vývoj aplikací .NET využívajících více kontejnerů a mikroslužeb
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Seznamte se s externí architekturou pro navrhování a vývoj aplikací .NET využívajících více kontejnerů a mikroslužeb.
ms.date: 10/02/2018
ms.openlocfilehash: 8c2f828e9913a0efcdf580371124b0f624daeffe
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296624"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a><span data-ttu-id="fbf0a-103">Navrhování a vývoj aplikací .NET založených na více kontejnerech a mikroslužbách</span><span class="sxs-lookup"><span data-stu-id="fbf0a-103">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>

<span data-ttu-id="fbf0a-104">*Vývoj kontejnerových aplikací s využitím kontejnerů znamená, že vytváříte aplikace s více kontejnery. Aplikace s více kontejnery by ale mohla být jednodušší, například aplikace se třemi vrstvami – a nemusí být sestavená pomocí architektury mikroslužeb.*</span><span class="sxs-lookup"><span data-stu-id="fbf0a-104">*Developing containerized microservice applications means you are building multi-container applications. However, a multi-container application could also be simpler—for example, a three-tier application—and might not be built using a microservice architecture.*</span></span>

<span data-ttu-id="fbf0a-105">Dříve jsme při vytváření architektury mikroslužeb vyvolali otázku "Docker".</span><span class="sxs-lookup"><span data-stu-id="fbf0a-105">Earlier we raised the question "Is Docker necessary when building a microservice architecture?"</span></span> <span data-ttu-id="fbf0a-106">Odpověď není jasné.</span><span class="sxs-lookup"><span data-stu-id="fbf0a-106">The answer is a clear no.</span></span> <span data-ttu-id="fbf0a-107">Docker je aktivátor a může poskytovat významné výhody, ale kontejnery a Docker nejsou pro mikroslužby pevně nutné.</span><span class="sxs-lookup"><span data-stu-id="fbf0a-107">Docker is an enabler and can provide significant benefits, but containers and Docker are not a hard requirement for microservices.</span></span> <span data-ttu-id="fbf0a-108">Jako příklad můžete vytvořit aplikaci založenou na mikroslužbách s Docker nebo bez něj při použití Azure Service Fabric, která podporuje mikroslužby spuštěné jako jednoduché procesy nebo jako kontejnery Docker.</span><span class="sxs-lookup"><span data-stu-id="fbf0a-108">As an example, you could create a microservices-based application with or without Docker when using Azure Service Fabric, which supports microservices running as simple processes or as Docker containers.</span></span>

<span data-ttu-id="fbf0a-109">Pokud ale víte, jak navrhnout a vyvíjet aplikaci založenou na mikroslužbách, která je založená na kontejnerech Docker, budete moct navrhnout a vyvíjet jakýkoliv jiný, jednodušší aplikační model.</span><span class="sxs-lookup"><span data-stu-id="fbf0a-109">However, if you know how to design and develop a microservices-based application that is also based on Docker containers, you will be able to design and develop any other, simpler application model.</span></span> <span data-ttu-id="fbf0a-110">Můžete například navrhnout trojrozměrnou aplikaci, která také vyžaduje přístup přes více kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="fbf0a-110">For example, you might design a three-tier application that also requires a multi-container approach.</span></span> <span data-ttu-id="fbf0a-111">Vzhledem k tomu, že architektury mikroslužeb jsou důležitým trendem v rámci kontejneru světa, se tato část zaměřuje na implementaci architektury mikroslužeb pomocí kontejnerů Docker.</span><span class="sxs-lookup"><span data-stu-id="fbf0a-111">Because of that, and because microservice architectures are an important trend within the container world, this section focuses on a microservice architecture implementation using Docker containers.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fbf0a-112">[Předchozí](../docker-application-development-process/docker-app-development-workflow.md)
>[Další](microservice-application-design.md)</span><span class="sxs-lookup"><span data-stu-id="fbf0a-112">[Previous](../docker-application-development-process/docker-app-development-workflow.md)
[Next](microservice-application-design.md)</span></span>
