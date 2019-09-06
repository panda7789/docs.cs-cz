---
title: Implementace odolných aplikací
description: Přečtěte si o odolnosti, klíčové koncepci v architektuře mikroslužeb. Musíte znát, jak plynule řešit přechodné chyby, protože k nim dojde.
ms.date: 10/16/2018
ms.openlocfilehash: 766349e72389f848b0a741b020707cc7acf3410d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296058"
---
# <a name="implement-resilient-applications"></a><span data-ttu-id="b40ea-104">Implementace odolných aplikací</span><span class="sxs-lookup"><span data-stu-id="b40ea-104">Implement Resilient Applications</span></span>

<span data-ttu-id="b40ea-105">*Vaše mikroslužby a cloudové aplikace musí vycházet z částečně neúspěšných selhání. Je nutné navrhnout aplikaci, která bude odolná vůči těmto částečným selháním.*</span><span class="sxs-lookup"><span data-stu-id="b40ea-105">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You must design your application to be resilient to those partial failures.*</span></span>

<span data-ttu-id="b40ea-106">Odolnost proti chybám je schopnost zotavení po selháních a nadále fungovat.</span><span class="sxs-lookup"><span data-stu-id="b40ea-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="b40ea-107">Nejedná se o předcházení chybám, ale přijímá skutečnost, že k selhání dojde a reagují na ně způsobem, který brání výpadkům nebo ztrátě dat.</span><span class="sxs-lookup"><span data-stu-id="b40ea-107">It isn't about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="b40ea-108">Cílem odolnosti proti chybám je vrátit aplikaci do plně funkčního stavu po selhání.</span><span class="sxs-lookup"><span data-stu-id="b40ea-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="b40ea-109">Pro návrh a nasazení aplikace založené na mikroslužbách je to dost náročné.</span><span class="sxs-lookup"><span data-stu-id="b40ea-109">It's challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="b40ea-110">Ale také je potřeba, aby vaše aplikace běžela v prostředí, kde je nějaký konkrétní druh selhání.</span><span class="sxs-lookup"><span data-stu-id="b40ea-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="b40ea-111">Proto by vaše aplikace měla být odolná.</span><span class="sxs-lookup"><span data-stu-id="b40ea-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="b40ea-112">Měla by být navržená tak, aby se vypořádat s částečnými chybami, jako jsou výpadky sítě nebo uzly nebo selhání virtuálních počítačů v cloudu.</span><span class="sxs-lookup"><span data-stu-id="b40ea-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="b40ea-113">Dokonce i mikroslužby (kontejnery), které se přesunou do jiného uzlu v clusteru, můžou v rámci aplikace způsobit přerušované krátké chyby.</span><span class="sxs-lookup"><span data-stu-id="b40ea-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="b40ea-114">Mnohé jednotlivé komponenty vaší aplikace by měly také zahrnovat funkce monitorování stavu.</span><span class="sxs-lookup"><span data-stu-id="b40ea-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="b40ea-115">Podle pokynů v této kapitole můžete vytvořit aplikaci, která může hladce fungovat navzdory přechodnému výpadku nebo normálním hiccups, ke kterým dochází ve složitých i cloudových nasazeních.</span><span class="sxs-lookup"><span data-stu-id="b40ea-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b40ea-116">[Předchozí](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)Další
>[](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="b40ea-116">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>
