---
title: Implementace odolných aplikací
description: Seznamte se s odolností, základní koncept v architektuře mikroslužeb. Musíte vědět, jak řádně zacházet s přechodnými chybami, když k nim dojde.
ms.date: 01/30/2020
ms.openlocfilehash: 46276a6b9b36a494bfae657275692ca9d5554d86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78847229"
---
# <a name="implement-resilient-applications"></a><span data-ttu-id="5867f-104">Implementace odolných aplikací</span><span class="sxs-lookup"><span data-stu-id="5867f-104">Implement resilient applications</span></span>

<span data-ttu-id="5867f-105">*Vaše mikroslužby a cloudové aplikace musí zahrnovat částečné chyby, které jistě dojde nakonec. Je nutné navrhnout aplikaci, aby byla odolná vůči těmto částečným selháním.*</span><span class="sxs-lookup"><span data-stu-id="5867f-105">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You must design your application to be resilient to those partial failures.*</span></span>

<span data-ttu-id="5867f-106">Odolnost proti chybám je schopnost zotavit se z chyb a nadále fungovat.</span><span class="sxs-lookup"><span data-stu-id="5867f-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="5867f-107">Nejde o to vyhnout se chybám, ale přijmout skutečnost, že k selháním dojde, a reagovat na ně způsobem, který zabraňuje výpadkům nebo ztrátě dat.</span><span class="sxs-lookup"><span data-stu-id="5867f-107">It isn't about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="5867f-108">Cílem odolnosti proti chybám je vrátit aplikaci do plně funkčního stavu po selhání.</span><span class="sxs-lookup"><span data-stu-id="5867f-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="5867f-109">Je dostatečně náročné navrhnout a nasadit aplikaci založenou na mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="5867f-109">It's challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="5867f-110">Ale také je nutné zachovat aplikace spuštěna v prostředí, kde je jistý nějaký druh selhání.</span><span class="sxs-lookup"><span data-stu-id="5867f-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="5867f-111">Proto by měla být vaše aplikace odolná.</span><span class="sxs-lookup"><span data-stu-id="5867f-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="5867f-112">Měl by být navržen tak, aby se vypořádal s částečnými chybami, jako jsou výpadky sítě nebo uzly nebo virtuální počítače, které se v cloudu zhroutí.</span><span class="sxs-lookup"><span data-stu-id="5867f-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="5867f-113">I mikroslužeb (kontejnery) přesouvána do jiného uzlu v rámci clusteru může způsobit občasné krátké chyby v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="5867f-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="5867f-114">Mnoho jednotlivých součástí aplikace by měly také obsahovat funkce monitorování stavu.</span><span class="sxs-lookup"><span data-stu-id="5867f-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="5867f-115">Podle pokynů v této kapitole můžete vytvořit aplikaci, která může pracovat hladce i přes přechodné prostoje nebo normální škytavka, ke kterým dochází ve složitých a cloudových nasazeních.</span><span class="sxs-lookup"><span data-stu-id="5867f-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="5867f-116">EShopOnContainer používal [knihovnu Polly](http://www.thepollyproject.org/) k implementaci odolnosti pomocí [zadaliklientů](./use-httpclientfactory-to-implement-resilient-http-requests.md) až do vydání 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="5867f-116">eShopOnContainer had been using the [Polly library](http://www.thepollyproject.org/) to implement resiliency using [Typed Clients](./use-httpclientfactory-to-implement-resilient-http-requests.md) up until the release 3.0.0.</span></span>
>
> <span data-ttu-id="5867f-117">Počínaje verzí 3.0.0 je vynuceno odolnost volání HTTP pomocí [sítě Linkerd](https://linkerd.io/), která zpracovává opakované pokusy transparentním a konfigurovatelným způsobem v rámci clusteru Kubernetes, aniž by bylo třeba zpracovávat tyto problémy v kódu.</span><span class="sxs-lookup"><span data-stu-id="5867f-117">Starting with release 3.0.0, the HTTP calls resiliency is implemented using a [Linkerd mesh](https://linkerd.io/), that handles retries in a transparent and configurable fashion, within a Kubernetes cluster, without having to handle those concerns in the code.</span></span>
>
> <span data-ttu-id="5867f-118">Knihovna Polly se stále používá k přidání odolnosti k databázovým připojením, zvláště při spouštění služeb.</span><span class="sxs-lookup"><span data-stu-id="5867f-118">The Polly library is still used to add resilience to database connections, specially while starting up the services.</span></span>

>[!WARNING]
> <span data-ttu-id="5867f-119">Všechny ukázky kódu v této části byly platné před použitím Linkerd a nejsou aktualizovány tak, aby odrážely aktuální skutečný kód.</span><span class="sxs-lookup"><span data-stu-id="5867f-119">All code samples in this section were valid before using Linkerd and are not updated to reflect the current actual code.</span></span> <span data-ttu-id="5867f-120">Takže mají smysl v kontextu této sekce.</span><span class="sxs-lookup"><span data-stu-id="5867f-120">So they make sense in the context of this section.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5867f-121">[Předchozí](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[další](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="5867f-121">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>
