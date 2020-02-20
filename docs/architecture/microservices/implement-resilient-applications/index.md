---
title: Implementace odolných aplikací
description: Přečtěte si o odolnosti, klíčové koncepci v architektuře mikroslužeb. Musíte znát, jak plynule řešit přechodné chyby, když k nim dojde.
ms.date: 01/30/2020
ms.openlocfilehash: ccdb2470c727ad4bd89c4e0634da8564b8010e63
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502658"
---
# <a name="implement-resilient-applications"></a><span data-ttu-id="f54b1-104">Implementace odolných aplikací</span><span class="sxs-lookup"><span data-stu-id="f54b1-104">Implement resilient applications</span></span>

<span data-ttu-id="f54b1-105">*Vaše mikroslužby a cloudové aplikace musí vycházet z částečně neúspěšných selhání. Je nutné navrhnout aplikaci, která bude odolná vůči těmto částečným selháním.*</span><span class="sxs-lookup"><span data-stu-id="f54b1-105">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You must design your application to be resilient to those partial failures.*</span></span>

<span data-ttu-id="f54b1-106">Odolnost proti chybám je schopnost zotavení po selháních a nadále fungovat.</span><span class="sxs-lookup"><span data-stu-id="f54b1-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="f54b1-107">Nejedná se o předcházení chybám, ale přijímá skutečnost, že k selhání dojde a reagují na ně způsobem, který brání výpadkům nebo ztrátě dat.</span><span class="sxs-lookup"><span data-stu-id="f54b1-107">It isn't about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="f54b1-108">Cílem odolnosti proti chybám je vrátit aplikaci do plně funkčního stavu po selhání.</span><span class="sxs-lookup"><span data-stu-id="f54b1-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="f54b1-109">Pro návrh a nasazení aplikace založené na mikroslužbách je to dost náročné.</span><span class="sxs-lookup"><span data-stu-id="f54b1-109">It's challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="f54b1-110">Ale také je potřeba, aby vaše aplikace běžela v prostředí, kde je nějaký konkrétní druh selhání.</span><span class="sxs-lookup"><span data-stu-id="f54b1-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="f54b1-111">Proto by vaše aplikace měla být odolná.</span><span class="sxs-lookup"><span data-stu-id="f54b1-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="f54b1-112">Měla by být navržená tak, aby se vypořádat s částečnými chybami, jako jsou výpadky sítě nebo uzly nebo selhání virtuálních počítačů v cloudu.</span><span class="sxs-lookup"><span data-stu-id="f54b1-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="f54b1-113">Dokonce i mikroslužby (kontejnery), které se přesunou do jiného uzlu v clusteru, můžou v rámci aplikace způsobit přerušované krátké chyby.</span><span class="sxs-lookup"><span data-stu-id="f54b1-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="f54b1-114">Mnohé jednotlivé komponenty vaší aplikace by měly také zahrnovat funkce monitorování stavu.</span><span class="sxs-lookup"><span data-stu-id="f54b1-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="f54b1-115">Podle pokynů v této kapitole můžete vytvořit aplikaci, která může hladce fungovat navzdory přechodnému výpadku nebo normálním hiccups, ke kterým dochází ve složitých i cloudových nasazeních.</span><span class="sxs-lookup"><span data-stu-id="f54b1-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="f54b1-116">eShopOnContainer používala [knihovnu Polly](http://www.thepollyproject.org/) k implementaci odolnosti pomocí [typových klientů](./use-httpclientfactory-to-implement-resilient-http-requests.md) až do vydání 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="f54b1-116">eShopOnContainer had been using the [Polly library](http://www.thepollyproject.org/) to implement resiliency using [Typed Clients](./use-httpclientfactory-to-implement-resilient-http-requests.md) up until the release 3.0.0.</span></span>
>
> <span data-ttu-id="f54b1-117">Od verze 3.0.0 je odolnost volání HTTP implementovaná pomocí [propojovací sítě](https://linkerd.io/), která zpracovává opakované pokusy transparentním a konfigurovatelným způsobem v rámci clusteru Kubernetes, aniž by bylo nutné tyto obavy v kódu zpracovat.</span><span class="sxs-lookup"><span data-stu-id="f54b1-117">Starting with release 3.0.0, the HTTP calls resiliency is implemented using a [Linkerd mesh](https://linkerd.io/), that handles retries in transparent and configurable fashion, within a Kubernetes cluster, without having to handle those concerns in the code.</span></span>
>
> <span data-ttu-id="f54b1-118">Knihovna Polly se pořád používá k přidání odolnosti do databázových připojení, která jsou speciálně při spouštění služeb.</span><span class="sxs-lookup"><span data-stu-id="f54b1-118">The Polly library is still used to add resilience to database connections, specially while starting up the services.</span></span>

>[!WARNING]
> <span data-ttu-id="f54b1-119">Všechny ukázky kódu v této části byly platné před použitím linkeru a nejsou aktualizovány, aby odrážely aktuální vlastní kód.</span><span class="sxs-lookup"><span data-stu-id="f54b1-119">All code samples in this section were valid before using Linkerd and are not updated to reflect the current actual code.</span></span> <span data-ttu-id="f54b1-120">Proto dávají smysl v kontextu této části.</span><span class="sxs-lookup"><span data-stu-id="f54b1-120">So they make sense in the context of this section.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f54b1-121">[Předchozí](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[Další](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="f54b1-121">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>
