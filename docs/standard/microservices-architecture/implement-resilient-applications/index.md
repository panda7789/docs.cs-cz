---
title: Implementace odolná aplikace
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace odolná aplikace
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ddb0f54b15735b9192d2088495947588f59829a0
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106048"
---
# <a name="implementing-resilient-applications"></a><span data-ttu-id="67d47-103">Implementace odolná aplikace</span><span class="sxs-lookup"><span data-stu-id="67d47-103">Implementing Resilient Applications</span></span>

<span data-ttu-id="67d47-104">*Vaše mikroslužbu a cloudové aplikace musí použít částečný chyby, ke kterým určitě dojde nakonec. Je třeba navrhnout vaše aplikace, bude odolné vůči selhání těchto částečné.*</span><span class="sxs-lookup"><span data-stu-id="67d47-104">*Your microservice and cloud based applications must embrace the partial failures that will certainly occur eventually. You need to design your application so it will be resilient to those partial failures.*</span></span>

<span data-ttu-id="67d47-105">Odolnost proti chybám je možnost obnovení v případě selhání a i nadále fungovat.</span><span class="sxs-lookup"><span data-stu-id="67d47-105">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="67d47-106">Nejedná se o zamezení selhání, ale přijímá fakt, že dojde k selhání a reagovat na ně způsobem, který zabraňuje výpadku nebo ztráty dat.</span><span class="sxs-lookup"><span data-stu-id="67d47-106">It is not about avoiding failures, but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="67d47-107">Cílem odolnosti je pro návrat aplikace plně funkčního stavu po selhání.</span><span class="sxs-lookup"><span data-stu-id="67d47-107">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="67d47-108">Je náročné dost pro návrh a nasazení aplikace na základě mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="67d47-108">It is challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="67d47-109">Ale musíte také zachovat spuštěn v prostředí, kde některé řazení selhání je určitá aplikace.</span><span class="sxs-lookup"><span data-stu-id="67d47-109">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="67d47-110">Aplikace musí být proto odolný.</span><span class="sxs-lookup"><span data-stu-id="67d47-110">Therefore, your application should be resilient.</span></span> <span data-ttu-id="67d47-111">Ho by se měly navrhovat zvládnout s částečné chybami, jako jsou výpadky sítě nebo uzly nebo chybám v cloudu virtuálních počítačů.</span><span class="sxs-lookup"><span data-stu-id="67d47-111">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="67d47-112">Přesouvá na jiný uzel v clusteru i mikroslužeb (kontejnerů) může způsobit občasné krátké chyby v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="67d47-112">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="67d47-113">Mnoho jednotlivých součástí aplikace by měla obsahovat také funkce sledování stavu.</span><span class="sxs-lookup"><span data-stu-id="67d47-113">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="67d47-114">Podle pokynů v této kapitole můžete vytvořit aplikaci, která může bezproblémově pracovat s Přestože přechodný výpadku nebo normální hiccups, ke kterým došlo v nasazení komplexní a založené na cloudu.</span><span class="sxs-lookup"><span data-stu-id="67d47-114">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="67d47-115">[Předchozí](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[další](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="67d47-115">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>
