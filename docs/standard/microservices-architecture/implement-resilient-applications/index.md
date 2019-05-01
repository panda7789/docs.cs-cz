---
title: Implementace odolných aplikací
description: Další informace o odolnost, základní pojmy v architektuře mikroslužeb. Musíte vědět, jak řešit přechodná selhání bez výpadku, protože se k nim dojde.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 00724509ba6e027ef73f72bfb6f85b8ec0aa9d25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61977700"
---
# <a name="implement-resilient-applications"></a><span data-ttu-id="a5381-104">Implementace odolných aplikací</span><span class="sxs-lookup"><span data-stu-id="a5381-104">Implement Resilient Applications</span></span>

<span data-ttu-id="a5381-105">*Částečně neúspěšné, kterým bude určitě nakonec musí využívat mikroslužeb a cloudových aplikací. Je třeba navrhnout aplikaci chcete být odolní vůči selhání v těchto částečné.*</span><span class="sxs-lookup"><span data-stu-id="a5381-105">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You must design your application to be resilient to those partial failures.*</span></span>

<span data-ttu-id="a5381-106">Odolnost proti chybám je schopnost zotavení z chyb a nadále fungovat.</span><span class="sxs-lookup"><span data-stu-id="a5381-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="a5381-107">Nejedná se o předcházení chybám, ale přijímá skutečnost, že dojde k selhání a reagovat na ně způsobem, který zabraňuje výpadkům nebo ztrátě.</span><span class="sxs-lookup"><span data-stu-id="a5381-107">It isn't about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="a5381-108">Cílem odolnosti proti chybám je plně funkčního stavu aplikace po selhání.</span><span class="sxs-lookup"><span data-stu-id="a5381-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="a5381-109">Je náročné dost informací k návrhu a nasazení aplikací založených na mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="a5381-109">It's challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="a5381-110">Ale je také potřeba nechat běžící v prostředí, kde nějaký druh selhání je určitá aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5381-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="a5381-111">Proto se vaše aplikace by měl být odolný.</span><span class="sxs-lookup"><span data-stu-id="a5381-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="a5381-112">To by se měly navrhovat pro zvládnutí částečné selhání, jako je výpadek sítě nebo uzly nebo virtuální počítače k chybám v cloudu.</span><span class="sxs-lookup"><span data-stu-id="a5381-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="a5381-113">Dokonce i mikroslužby (kontejnerů) přesouvá na jiný uzel v rámci clusteru může způsobit krátkodobých krátká selhání v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5381-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="a5381-114">Mnoho jednotlivých komponent vaší aplikace by měly zahrnovat taky funkce monitorování stavu.</span><span class="sxs-lookup"><span data-stu-id="a5381-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="a5381-115">Pomocí následujících pokynů v této kapitole, můžete vytvořit aplikace, které může fungovat bez problémů, přestože přechodné výpadky nebo normální bude odolný vůči kolísání, ke kterým dochází ve složitých a cloudové nasazení.</span><span class="sxs-lookup"><span data-stu-id="a5381-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a5381-116">[Předchozí](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[další](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="a5381-116">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>