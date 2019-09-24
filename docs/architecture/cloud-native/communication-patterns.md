---
title: Schémata komunikace nativní pro cloud
description: Další informace o komunikaci s klíčovou službou v cloudových nativních aplikacích
author: robvet
ms.date: 08/31/2019
ms.openlocfilehash: 3bda9baa516b7bd8f893e0f58bbe5e2bfde2b61d
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214016"
---
# <a name="cloud-native-communication-patterns"></a><span data-ttu-id="0157d-103">Schémata komunikace nativní pro cloud</span><span class="sxs-lookup"><span data-stu-id="0157d-103">Cloud-native communication patterns</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="0157d-104">Při sestavování nativního cloudového systému se komunikace stala významným rozhodnutím o návrhu.</span><span class="sxs-lookup"><span data-stu-id="0157d-104">When constructing a cloud-native system, communication becomes a significant design decision.</span></span> <span data-ttu-id="0157d-105">Jak klientská aplikace front-endu komunikuje s back-end mikroslužbami?</span><span class="sxs-lookup"><span data-stu-id="0157d-105">How does a front-end client application communicate with a back-end microservice?</span></span> <span data-ttu-id="0157d-106">Jak vzájemně komunikují mikroslužby back-end?</span><span class="sxs-lookup"><span data-stu-id="0157d-106">How do back-end microservices communicate with each other?</span></span> <span data-ttu-id="0157d-107">Jaké jsou zásady, vzory a osvědčené postupy, které je potřeba vzít v úvahu při implementaci komunikace v cloudových nativních aplikacích?</span><span class="sxs-lookup"><span data-stu-id="0157d-107">What are the principles, patterns, and best practices to consider when implementing communication in cloud-native applications?</span></span>

## <a name="communication-considerations"></a><span data-ttu-id="0157d-108">Otázky komunikace</span><span class="sxs-lookup"><span data-stu-id="0157d-108">Communication considerations</span></span>

<span data-ttu-id="0157d-109">V aplikaci monolitické je komunikace jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="0157d-109">In a monolithic application, communication is straightforward.</span></span> <span data-ttu-id="0157d-110">Kódové moduly se provádějí společně ve stejném spustitelném prostoru (procesu) na serveru.</span><span class="sxs-lookup"><span data-stu-id="0157d-110">The code modules execute together in the same executable space (process) on a server.</span></span> <span data-ttu-id="0157d-111">Tento přístup může mít vliv na výkon, protože všechno běží dohromady ve sdílené paměti, ale má za následek velmi složitý kód, který se může obtížně udržovat, vyvíjet a škálovat.</span><span class="sxs-lookup"><span data-stu-id="0157d-111">This approach can have performance advantages as everything runs together in shared memory, but results in tightly coupled code that becomes difficult to maintain, evolve, and scale.</span></span>

<span data-ttu-id="0157d-112">Cloudové nativní systémy implementují architekturu založenou na mikroslužbách s mnoha malými nezávislými mikroslužbami.</span><span class="sxs-lookup"><span data-stu-id="0157d-112">Cloud-native systems implement a microservice-based architecture with many small, independent microservices.</span></span> <span data-ttu-id="0157d-113">Každá mikroslužba se spouští v samostatném procesu a obvykle se spouští uvnitř kontejneru, který je nasazený do *clusteru*.</span><span class="sxs-lookup"><span data-stu-id="0157d-113">Each microservice executes in a separate process and typically runs inside a container that is deployed to a *cluster*.</span></span>

<span data-ttu-id="0157d-114">Cluster seskupuje fond virtuálních počítačů dohromady, aby bylo možné vytvořit vysoce dostupné prostředí.</span><span class="sxs-lookup"><span data-stu-id="0157d-114">A cluster groups a pool of virtual machines together to form a highly available environment.</span></span> <span data-ttu-id="0157d-115">Spravují se nástrojem orchestrace, který zodpovídá za nasazení a správu kontejnerových mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="0157d-115">They're managed with an orchestration tool, which is responsible for deploying and managing the containerized microservices.</span></span> <span data-ttu-id="0157d-116">Obrázek 4-1 ukazuje cluster [Kubernetes](https://kubernetes.io) nasazený do cloudu Azure s plně spravovanými [službami Azure Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes).</span><span class="sxs-lookup"><span data-stu-id="0157d-116">Figure 4-1 shows a [Kubernetes](https://kubernetes.io) cluster deployed into the Azure cloud with the fully managed [Azure Kubernetes Services](https://docs.microsoft.com/azure/aks/intro-kubernetes).</span></span>

![Cluster Kubernetes v Azure](./media/kubernetes-cluster-in-azure.png)

<span data-ttu-id="0157d-118">**Obrázek 4-1**.</span><span class="sxs-lookup"><span data-stu-id="0157d-118">**Figure 4-1**.</span></span> <span data-ttu-id="0157d-119">Cluster Kubernetes v Azure</span><span class="sxs-lookup"><span data-stu-id="0157d-119">A Kubernetes cluster in Azure</span></span>

<span data-ttu-id="0157d-120">Mezi clustery komunikuje mikroslužby vzájemně prostřednictvím rozhraní API a technologií zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="0157d-120">Across the cluster, microservices communicate with each other through APIs and messaging technologies.</span></span>

<span data-ttu-id="0157d-121">I když poskytují spoustu výhod, mikroslužby nejsou bezplatné na oběd.</span><span class="sxs-lookup"><span data-stu-id="0157d-121">While they provide many benefits, microservices are no free lunch.</span></span> <span data-ttu-id="0157d-122">Volání místní metody v procesu mezi komponentami jsou nyní nahrazena síťovými voláními.</span><span class="sxs-lookup"><span data-stu-id="0157d-122">Local in-process method calls between components are now replaced with network calls.</span></span> <span data-ttu-id="0157d-123">Každá mikroslužba musí komunikovat přes síťový protokol, což zvyšuje složitost vašeho systému:</span><span class="sxs-lookup"><span data-stu-id="0157d-123">Each microservice must communicate over a network protocol, which adds complexity to your system:</span></span>

- <span data-ttu-id="0157d-124">Při zahlcení sítě, latenci a přechodných chybách se jedná o konstantní problém.</span><span class="sxs-lookup"><span data-stu-id="0157d-124">Network congestion, latency, and transient faults are a constant concern.</span></span>

- <span data-ttu-id="0157d-125">Odolnost proti chybám (tj. opakování neúspěšných požadavků) je zásadní.</span><span class="sxs-lookup"><span data-stu-id="0157d-125">Resiliency (that is, retrying failed requests) is essential.</span></span>

- <span data-ttu-id="0157d-126">Některá volání musí být [idempotentní](https://www.restapitutorial.com/lessons/idempotency.html) , aby zachovala konzistentní stav.</span><span class="sxs-lookup"><span data-stu-id="0157d-126">Some calls must be [idempotent](https://www.restapitutorial.com/lessons/idempotency.html) as to keep consistent state.</span></span>

- <span data-ttu-id="0157d-127">Každá mikroslužba musí ověřovat a autorizovat volání.</span><span class="sxs-lookup"><span data-stu-id="0157d-127">Each microservice must authenticate and authorize calls.</span></span>

- <span data-ttu-id="0157d-128">Každou zprávu je nutné serializovat a pak deserializovat – což může být nákladné.</span><span class="sxs-lookup"><span data-stu-id="0157d-128">Each message must be serialized and then deserialized - which can be expensive.</span></span>

- <span data-ttu-id="0157d-129">Šifrování a dešifrování zpráv bude důležité.</span><span class="sxs-lookup"><span data-stu-id="0157d-129">Message encryption/decryption becomes important.</span></span>

<span data-ttu-id="0157d-130">Mikroslužby [Book .NET: Architektura pro kontejnerové aplikace](https://docs.microsoft.com/dotnet/standard/microservices-architecture/).NET, která je dostupná zdarma od Microsoftu, poskytuje podrobné pokrytí způsobů komunikace pro aplikace mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="0157d-130">The book [.NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/standard/microservices-architecture/), available for free from Microsoft, provides an in-depth coverage of communication patterns for microservice applications.</span></span> <span data-ttu-id="0157d-131">V této kapitole poskytujeme podrobný přehled těchto vzorů spolu s možnostmi implementace dostupnými v cloudu Azure.</span><span class="sxs-lookup"><span data-stu-id="0157d-131">In this chapter, we provide a high-level overview of these patterns along with implementation options available in the Azure cloud.</span></span>

<span data-ttu-id="0157d-132">V této kapitole budeme řešit komunikaci mezi front-end aplikacemi a back-endové mikroslužbami.</span><span class="sxs-lookup"><span data-stu-id="0157d-132">In this chapter, we'll first address communication between front-end applications and back-end microservices.</span></span> <span data-ttu-id="0157d-133">Pak se podíváme na back-endové mikroslužby, které navzájem komunikují.</span><span class="sxs-lookup"><span data-stu-id="0157d-133">We'll then look at back-end microservices communicate with each other.</span></span> <span data-ttu-id="0157d-134">Prozkoumáme komunikační technologii gRPC a.</span><span class="sxs-lookup"><span data-stu-id="0157d-134">We'll explore the up and gRPC communication technology.</span></span> <span data-ttu-id="0157d-135">Nakonec podíváme se na nové inovativní způsoby komunikace pomocí technologie sítě služby.</span><span class="sxs-lookup"><span data-stu-id="0157d-135">Finally, we'll look new innovative communication patterns using service mesh technology.</span></span> <span data-ttu-id="0157d-136">Ukážeme vám také, jak Cloud Azure poskytuje různé druhy *služeb* , které umožňují podporovat komunikaci v cloudu.</span><span class="sxs-lookup"><span data-stu-id="0157d-136">We'll also see how the Azure cloud provides different kinds of *backing services* to support cloud-native communication.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0157d-137">[Předchozí](other-deployment-options.md)
>[Další](front-end-communication.md)</span><span class="sxs-lookup"><span data-stu-id="0157d-137">[Previous](other-deployment-options.md)
[Next](front-end-communication.md)</span></span>
