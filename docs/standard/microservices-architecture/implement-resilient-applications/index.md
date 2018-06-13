---
title: Implementace odolná aplikace
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace odolná aplikace
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 211814eff0f2aaf0cf71a19cfcaaeb44924fb6f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573736"
---
# <a name="implementing-resilient-applications"></a><span data-ttu-id="78104-103">Implementace odolná aplikace</span><span class="sxs-lookup"><span data-stu-id="78104-103">Implementing Resilient Applications</span></span>

<span data-ttu-id="78104-104">*Vaše mikroslužbu a cloudové aplikace musí použít částečný chyby, ke kterým určitě dojde nakonec. Je třeba navrhnout vaše aplikace, bude odolné vůči selhání těchto částečné.*</span><span class="sxs-lookup"><span data-stu-id="78104-104">*Your microservice and cloud based applications must embrace the partial failures that will certainly occur eventually. You need to design your application so it will be resilient to those partial failures.*</span></span>

<span data-ttu-id="78104-105">Odolnost proti chybám je možnost obnovení v případě selhání a i nadále fungovat.</span><span class="sxs-lookup"><span data-stu-id="78104-105">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="78104-106">Nejedná se o zamezení selhání, ale přijímá fakt, že dojde k selhání a reagovat na ně způsobem, který zabraňuje výpadku nebo ztráty dat.</span><span class="sxs-lookup"><span data-stu-id="78104-106">It is not about avoiding failures, but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="78104-107">Cílem odolnosti je pro návrat aplikace plně funkčního stavu po selhání.</span><span class="sxs-lookup"><span data-stu-id="78104-107">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="78104-108">Je náročné dost pro návrh a nasazení aplikace na základě mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="78104-108">It is challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="78104-109">Ale musíte také zachovat spuštěn v prostředí, kde některé řazení selhání je určitá aplikace.</span><span class="sxs-lookup"><span data-stu-id="78104-109">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="78104-110">Aplikace musí být proto odolný.</span><span class="sxs-lookup"><span data-stu-id="78104-110">Therefore, your application should be resilient.</span></span> <span data-ttu-id="78104-111">Ho by se měly navrhovat zvládnout s částečné chybami, jako jsou výpadky sítě nebo uzly nebo chybám v cloudu virtuálních počítačů.</span><span class="sxs-lookup"><span data-stu-id="78104-111">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="78104-112">Přesouvá na jiný uzel v clusteru i mikroslužeb (kontejnerů) může způsobit občasné krátké chyby v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="78104-112">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="78104-113">Mnoho jednotlivých součástí aplikace by měla obsahovat také funkce sledování stavu.</span><span class="sxs-lookup"><span data-stu-id="78104-113">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="78104-114">Podle pokynů v této kapitole můžete vytvořit aplikaci, která může bezproblémově pracovat s Přestože přechodný výpadku nebo normální hiccups, ke kterým došlo v nasazení komplexní a založené na cloudu.</span><span class="sxs-lookup"><span data-stu-id="78104-114">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="78104-115">[Předchozí] (.. / microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [Další] (popisovač failure.md partial)</span><span class="sxs-lookup"><span data-stu-id="78104-115">[Previous] (../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [Next] (handle-partial-failure.md)</span></span>
