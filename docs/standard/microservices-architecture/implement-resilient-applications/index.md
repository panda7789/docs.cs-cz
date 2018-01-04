---
title: "Implementace odolná aplikace"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace odolná aplikace"
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
ms.openlocfilehash: 93e5435b402cc1a8ff049f25465de0f719516f31
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-resilient-applications"></a><span data-ttu-id="a77c7-104">Implementace odolná aplikace</span><span class="sxs-lookup"><span data-stu-id="a77c7-104">Implementing Resilient Applications</span></span>

<span data-ttu-id="a77c7-105">*Vaše mikroslužbu a cloudové aplikace musí použít částečný chyby, ke kterým určitě dojde nakonec. Je třeba navrhnout vaše aplikace, bude odolné vůči selhání těchto částečné.*</span><span class="sxs-lookup"><span data-stu-id="a77c7-105">*Your microservice and cloud based applications must embrace the partial failures that will certainly occur eventually. You need to design your application so it will be resilient to those partial failures.*</span></span>

<span data-ttu-id="a77c7-106">Odolnost proti chybám je možnost obnovení v případě selhání a i nadále fungovat.</span><span class="sxs-lookup"><span data-stu-id="a77c7-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="a77c7-107">Nejedná se o zamezení selhání, ale přijímá fakt, že dojde k selhání a reagovat na ně způsobem, který zabraňuje výpadku nebo ztráty dat.</span><span class="sxs-lookup"><span data-stu-id="a77c7-107">It is not about avoiding failures, but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="a77c7-108">Cílem odolnosti je pro návrat aplikace plně funkčního stavu po selhání.</span><span class="sxs-lookup"><span data-stu-id="a77c7-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="a77c7-109">Je náročné dost pro návrh a nasazení aplikace na základě mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="a77c7-109">It is challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="a77c7-110">Ale musíte také zachovat spuštěn v prostředí, kde některé řazení selhání je určitá aplikace.</span><span class="sxs-lookup"><span data-stu-id="a77c7-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="a77c7-111">Aplikace musí být proto odolný.</span><span class="sxs-lookup"><span data-stu-id="a77c7-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="a77c7-112">Ho by se měly navrhovat zvládnout s částečné chybami, jako jsou výpadky sítě nebo uzly nebo chybám v cloudu virtuálních počítačů.</span><span class="sxs-lookup"><span data-stu-id="a77c7-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="a77c7-113">Přesouvá na jiný uzel v clusteru i mikroslužeb (kontejnerů) může způsobit občasné krátké chyby v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a77c7-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="a77c7-114">Mnoho jednotlivých součástí aplikace by měla obsahovat také funkce sledování stavu.</span><span class="sxs-lookup"><span data-stu-id="a77c7-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="a77c7-115">Podle pokynů v této kapitole můžete vytvořit aplikaci, která může bezproblémově pracovat s Přestože přechodný výpadku nebo normální hiccups, ke kterým došlo v nasazení komplexní a založené na cloudu.</span><span class="sxs-lookup"><span data-stu-id="a77c7-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a77c7-116">[Předchozí] (.. / microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [Další] (popisovač failure.md partial)</span><span class="sxs-lookup"><span data-stu-id="a77c7-116">[Previous] (../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [Next] (handle-partial-failure.md)</span></span>
