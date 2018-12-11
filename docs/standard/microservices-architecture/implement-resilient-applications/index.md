---
title: Implementace odolných aplikací
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Implementace odolných aplikací
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: ec79221f0238d61f1ca1b2b7c58b1e16be7f4df4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130791"
---
# <a name="implementing-resilient-applications"></a><span data-ttu-id="628c4-103">Implementace odolných aplikací</span><span class="sxs-lookup"><span data-stu-id="628c4-103">Implementing Resilient Applications</span></span>

<span data-ttu-id="628c4-104">*Částečně neúspěšné, kterým bude určitě nakonec musí využívat mikroslužeb a cloudových aplikací. Je třeba navrhnout aplikace tak bude odolné vůči selhání v těchto částečné.*</span><span class="sxs-lookup"><span data-stu-id="628c4-104">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You need to design your application so it will be resilient to those partial failures.*</span></span>

<span data-ttu-id="628c4-105">Odolnost proti chybám je schopnost zotavení z chyb a nadále fungovat.</span><span class="sxs-lookup"><span data-stu-id="628c4-105">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="628c4-106">Nejedná se o předcházení chybám, ale přijímá skutečnost, že dojde k selhání a reagovat na ně způsobem, který zabraňuje výpadkům nebo ztrátě.</span><span class="sxs-lookup"><span data-stu-id="628c4-106">It is not about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="628c4-107">Cílem odolnosti proti chybám je plně funkčního stavu aplikace po selhání.</span><span class="sxs-lookup"><span data-stu-id="628c4-107">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="628c4-108">Je náročné dost informací k návrhu a nasazení aplikací založených na mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="628c4-108">It is challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="628c4-109">Ale je také potřeba nechat běžící v prostředí, kde nějaký druh selhání je určitá aplikace.</span><span class="sxs-lookup"><span data-stu-id="628c4-109">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="628c4-110">Proto se vaše aplikace by měl být odolný.</span><span class="sxs-lookup"><span data-stu-id="628c4-110">Therefore, your application should be resilient.</span></span> <span data-ttu-id="628c4-111">To by se měly navrhovat pro zvládnutí částečné selhání, jako je výpadek sítě nebo uzly nebo virtuální počítače k chybám v cloudu.</span><span class="sxs-lookup"><span data-stu-id="628c4-111">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="628c4-112">Dokonce i mikroslužby (kontejnerů) přesouvá na jiný uzel v rámci clusteru může způsobit krátkodobých krátká selhání v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="628c4-112">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="628c4-113">Mnoho jednotlivých komponent vaší aplikace by měly zahrnovat taky funkce monitorování stavu.</span><span class="sxs-lookup"><span data-stu-id="628c4-113">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="628c4-114">Pomocí následujících pokynů v této kapitole, můžete vytvořit aplikace, které může fungovat bez problémů, přestože přechodné výpadky nebo normální bude odolný vůči kolísání, ke kterým dochází ve složitých a cloudové nasazení.</span><span class="sxs-lookup"><span data-stu-id="628c4-114">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="628c4-115">[Předchozí](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[další](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="628c4-115">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>