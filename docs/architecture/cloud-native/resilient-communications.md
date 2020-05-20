---
title: Odolná komunikace
description: Architekt cloudových nativních aplikací .NET pro Azure | Odolná komunikace
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 33e4c03c1f3d8c01f72c588326fbb0bdfa512cdd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613743"
---
# <a name="resilient-communications"></a><span data-ttu-id="f8665-103">Odolná komunikace</span><span class="sxs-lookup"><span data-stu-id="f8665-103">Resilient communications</span></span>

<span data-ttu-id="f8665-104">V celé této příručce jsme dělali přístup k architektuře založené na mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="f8665-104">Throughout this book, we've embraced a microservice-based architectural approach.</span></span> <span data-ttu-id="f8665-105">I když taková architektura přináší důležité výhody, představuje mnoho výzev:</span><span class="sxs-lookup"><span data-stu-id="f8665-105">While such an architecture provides important benefits, it presents many challenges:</span></span>

- <span data-ttu-id="f8665-106">*Neprocesová síťová komunikace.*</span><span class="sxs-lookup"><span data-stu-id="f8665-106">*Out-of-process network communication.*</span></span> <span data-ttu-id="f8665-107">Každá mikroslužba komunikuje přes síťový protokol, který zavádí zahlcení sítě, latenci a přechodné chyby.</span><span class="sxs-lookup"><span data-stu-id="f8665-107">Each microservice communicates over a network protocol that introduces network congestion, latency, and transient faults.</span></span>

- <span data-ttu-id="f8665-108">*Zjišťování služby.*</span><span class="sxs-lookup"><span data-stu-id="f8665-108">*Service discovery.*</span></span> <span data-ttu-id="f8665-109">Jak mikroslužby zjišťují a vzájemně komunikují při provozu v clusteru počítačů s vlastními IP adresami a porty?</span><span class="sxs-lookup"><span data-stu-id="f8665-109">How do microservices discover and communicate with each other when running across a cluster of machines with their own IP addresses and ports?</span></span>

- <span data-ttu-id="f8665-110">*Odolnost.*</span><span class="sxs-lookup"><span data-stu-id="f8665-110">*Resiliency.*</span></span> <span data-ttu-id="f8665-111">Jak se spravují krátkodobé nenáročné chyby a systém udržuje stabilní?</span><span class="sxs-lookup"><span data-stu-id="f8665-111">How do you manage short-lived failures and keep the system stable?</span></span>

- <span data-ttu-id="f8665-112">*Vyrovnávání zatížení.*</span><span class="sxs-lookup"><span data-stu-id="f8665-112">*Load balancing.*</span></span> <span data-ttu-id="f8665-113">Jak se příchozí provoz rozděluje napříč víc instancemi mikroslužeb?</span><span class="sxs-lookup"><span data-stu-id="f8665-113">How does inbound traffic get distributed across multiple instances of a microservice?</span></span>

- <span data-ttu-id="f8665-114">*Bezpečnost.*</span><span class="sxs-lookup"><span data-stu-id="f8665-114">*Security.*</span></span> <span data-ttu-id="f8665-115">Jak se týká zabezpečení, jako je šifrování na úrovni přenosu a Správa certifikátů?</span><span class="sxs-lookup"><span data-stu-id="f8665-115">How are security concerns such as transport-level encryption and certificate management enforced?</span></span>

- <span data-ttu-id="f8665-116">*Distribuované monitorování.*</span><span class="sxs-lookup"><span data-stu-id="f8665-116">*Distributed Monitoring.*</span></span> <span data-ttu-id="f8665-117">– Jak korelujete a zachytíte sledovatelnost a monitorování pro jeden požadavek napříč několika náročnými mikroslužbami?</span><span class="sxs-lookup"><span data-stu-id="f8665-117">- How do you correlate and capture traceability and monitoring for a single request across multiple consuming microservices?</span></span>

<span data-ttu-id="f8665-118">Tyto aspekty můžete vyřešit pomocí různých knihoven a architektur, ale implementace může být náročná, složitá a časově náročná.</span><span class="sxs-lookup"><span data-stu-id="f8665-118">You can address these concerns with different libraries and frameworks, but the implementation can be expensive, complex, and time-consuming.</span></span> <span data-ttu-id="f8665-119">I když máte i nadále problémy s infrastrukturou, která je spojená s obchodní logikou.</span><span class="sxs-lookup"><span data-stu-id="f8665-119">You also end up with infrastructure concerns coupled to business logic.</span></span>

## <a name="service-mesh"></a><span data-ttu-id="f8665-120">Síť sítě</span><span class="sxs-lookup"><span data-stu-id="f8665-120">Service mesh</span></span>

<span data-ttu-id="f8665-121">Lepším přístupem je vyvíjející se technologie s názvem *sítě*.</span><span class="sxs-lookup"><span data-stu-id="f8665-121">A better approach is an evolving technology entitled *Service Mesh*.</span></span> <span data-ttu-id="f8665-122">[Síť](https://www.nginx.com/blog/what-is-a-service-mesh/) je konfigurovatelná vrstva infrastruktury s integrovanými možnostmi pro zpracování komunikace služby a dalších výzev uvedených výše.</span><span class="sxs-lookup"><span data-stu-id="f8665-122">A [service mesh](https://www.nginx.com/blog/what-is-a-service-mesh/) is a configurable infrastructure layer with built-in capabilities to handle service communication and the other challenges mentioned above.</span></span> <span data-ttu-id="f8665-123">Tyto otázky se oddělí přesunutím na proxy služby.</span><span class="sxs-lookup"><span data-stu-id="f8665-123">It decouples these concerns by moving them into a service proxy.</span></span> <span data-ttu-id="f8665-124">Proxy server se nasadí do samostatného procesu (označovaného jako [postranní vozík](https://docs.microsoft.com/azure/architecture/patterns/sidecar)), aby poskytoval izolaci od obchodního kódu.</span><span class="sxs-lookup"><span data-stu-id="f8665-124">The proxy is deployed into a separate process (called a [sidecar](https://docs.microsoft.com/azure/architecture/patterns/sidecar)) to provide isolation from business code.</span></span> <span data-ttu-id="f8665-125">Tento postranní vozík je ale spojený s touto službou – vytvoří se s ním a sdílí životní cyklus.</span><span class="sxs-lookup"><span data-stu-id="f8665-125">However, the sidecar is linked to the service - it's created with it and shares its lifecycle.</span></span> <span data-ttu-id="f8665-126">Obrázek 6-7 ukazuje tento scénář.</span><span class="sxs-lookup"><span data-stu-id="f8665-126">Figure 6-7 shows this scenario.</span></span>

![Síť s postranním vozíkem](./media/service-mesh-with-side-car.png)

<span data-ttu-id="f8665-128">**Obrázek 6-7**.</span><span class="sxs-lookup"><span data-stu-id="f8665-128">**Figure 6-7**.</span></span> <span data-ttu-id="f8665-129">Síť s postranním vozíkem</span><span class="sxs-lookup"><span data-stu-id="f8665-129">Service mesh with a side car</span></span>

<span data-ttu-id="f8665-130">Na předchozím obrázku si všimněte, jak proxy zachytí a spravuje komunikaci mezi mikroslužbami a clusterem.</span><span class="sxs-lookup"><span data-stu-id="f8665-130">In the previous figure, note how the proxy intercepts and manages communication among the microservices and the cluster.</span></span>

<span data-ttu-id="f8665-131">Síť je logicky rozdělená na dvě různorodé komponenty: [rovina dat](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) a [rovina ovládacího prvku](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc).</span><span class="sxs-lookup"><span data-stu-id="f8665-131">A service mesh is logically split into two disparate components: A [data plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) and [control plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc).</span></span> <span data-ttu-id="f8665-132">Obrázek 6-8 ukazuje tyto komponenty a jejich zodpovědnosti.</span><span class="sxs-lookup"><span data-stu-id="f8665-132">Figure 6-8 shows these components and their responsibilities.</span></span>

![Ovládací prvek sítě a rovina dat](./media/istio-control-and-data-plane.png)

<span data-ttu-id="f8665-134">**Obrázek 6-8.**</span><span class="sxs-lookup"><span data-stu-id="f8665-134">**Figure 6-8.**</span></span> <span data-ttu-id="f8665-135">Ovládací prvek sítě a rovina dat</span><span class="sxs-lookup"><span data-stu-id="f8665-135">Service mesh control and data plane</span></span>

<span data-ttu-id="f8665-136">Po nakonfigurování je síť velmi funkční.</span><span class="sxs-lookup"><span data-stu-id="f8665-136">Once configured, a service mesh is highly functional.</span></span> <span data-ttu-id="f8665-137">Může načíst odpovídající fond instancí z koncového bodu zjišťování služby.</span><span class="sxs-lookup"><span data-stu-id="f8665-137">It can retrieve a corresponding pool of instances from a service discovery endpoint.</span></span> <span data-ttu-id="f8665-138">Síť pak může poslat požadavek na konkrétní instanci, která zaznamená latenci a typ odpovědi výsledku.</span><span class="sxs-lookup"><span data-stu-id="f8665-138">The mesh can then send a request to a specific instance, recording the latency and response type of the result.</span></span> <span data-ttu-id="f8665-139">Síť může zvolit instanci, která pravděpodobně vrátí rychlou odpověď na základě mnoha faktorů, včetně pozorované latence pro poslední požadavky.</span><span class="sxs-lookup"><span data-stu-id="f8665-139">A mesh can choose the instance most likely to return a fast response based on many factors, including its observed latency for recent requests.</span></span>

<span data-ttu-id="f8665-140">Pokud instance nereaguje nebo se nezdaří, síť zopakuje požadavek na jiné instanci.</span><span class="sxs-lookup"><span data-stu-id="f8665-140">If an instance is unresponsive or fails, the mesh will retry the request on another instance.</span></span> <span data-ttu-id="f8665-141">Pokud dojde k chybám, síť vyřadí instanci z fondu vyrovnávání zatížení a po tom, co je zavede, ji obnoví.</span><span class="sxs-lookup"><span data-stu-id="f8665-141">If it returns errors, a mesh will evict the instance from the load-balancing pool and restate it after it heals.</span></span> <span data-ttu-id="f8665-142">Pokud vyprší časový limit požadavku, může dojít k selhání sítě a pak požadavek opakujte.</span><span class="sxs-lookup"><span data-stu-id="f8665-142">If a request times out, a mesh can fail and then retry the request.</span></span> <span data-ttu-id="f8665-143">Síť vychytí a vysílá metriky a distribuované trasování do centralizovaného systému metrik.</span><span class="sxs-lookup"><span data-stu-id="f8665-143">A mesh captures and emits metrics and distributed tracing to a centralized metrics system.</span></span>

## <a name="istio-and-envoy"></a><span data-ttu-id="f8665-144">Istio a zástupné</span><span class="sxs-lookup"><span data-stu-id="f8665-144">Istio and Envoy</span></span>

<span data-ttu-id="f8665-145">I když existuje několik možností sítě, které aktuálně existují, [Istio](https://istio.io/docs/concepts/what-is-istio/) je nejoblíbenější v době psaní tohoto textu.</span><span class="sxs-lookup"><span data-stu-id="f8665-145">While a few service mesh options currently exist, [Istio](https://istio.io/docs/concepts/what-is-istio/) is the most popular at the time of this writing.</span></span> <span data-ttu-id="f8665-146">Istio je společný podnik od IBM, Google a Lyft.</span><span class="sxs-lookup"><span data-stu-id="f8665-146">Istio is a joint venture from IBM, Google, and Lyft.</span></span> <span data-ttu-id="f8665-147">Jedná se o open-source nabídku, kterou je možné integrovat do nové nebo stávající distribuované aplikace.</span><span class="sxs-lookup"><span data-stu-id="f8665-147">It's an open-source offering that can be integrated into a new or existing distributed application.</span></span> <span data-ttu-id="f8665-148">Technologie poskytuje konzistentní a kompletní řešení pro zabezpečení, připojení a monitorování mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="f8665-148">The technology provides a consistent and complete solution to secure, connect, and monitor microservices.</span></span> <span data-ttu-id="f8665-149">Mezi tyto funkce patří:</span><span class="sxs-lookup"><span data-stu-id="f8665-149">Its features include:</span></span>

- <span data-ttu-id="f8665-150">Zabezpečená komunikace mezi službami v clusteru se silným ověřováním a autorizací na základě identity.</span><span class="sxs-lookup"><span data-stu-id="f8665-150">Secure service-to-service communication in a cluster with strong identity-based authentication and authorization.</span></span>
- <span data-ttu-id="f8665-151">Automatické vyrovnávání zatížení pro přenosy HTTP, [gRPC](https://grpc.io/), WebSocket a TCP.</span><span class="sxs-lookup"><span data-stu-id="f8665-151">Automatic load balancing for HTTP, [gRPC](https://grpc.io/), WebSocket, and TCP traffic.</span></span>
- <span data-ttu-id="f8665-152">Jemně odstupňovaná kontrola nad chováním provozu s bohatými pravidly směrování, opakovanými pokusy, převzetí služeb při selhání a vkládáním chyb.</span><span class="sxs-lookup"><span data-stu-id="f8665-152">Fine-grained control of traffic behavior with rich routing rules, retries, failovers, and fault injection.</span></span>
- <span data-ttu-id="f8665-153">Připojitelná vrstva zásad a konfigurační rozhraní API, které podporuje řízení přístupu, omezení přenosové rychlosti a kvóty.</span><span class="sxs-lookup"><span data-stu-id="f8665-153">A pluggable policy layer and configuration API supporting access controls, rate limits, and quotas.</span></span>
- <span data-ttu-id="f8665-154">Automatické metriky, protokoly a trasování pro veškerý provoz v rámci clusteru, včetně příchozího a odchozího clusteru.</span><span class="sxs-lookup"><span data-stu-id="f8665-154">Automatic metrics, logs, and traces for all traffic within a cluster, including cluster ingress and egress.</span></span>

<span data-ttu-id="f8665-155">Klíčovou komponentou pro implementaci Istio je proxy služba s oprávněním [proxy serveru zástupné](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy).</span><span class="sxs-lookup"><span data-stu-id="f8665-155">A key component for an Istio implementation is a proxy service entitled the [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy).</span></span> <span data-ttu-id="f8665-156">Spouští se spolu se všemi službami a poskytuje platformu nezávislá Foundation pro následující funkce:</span><span class="sxs-lookup"><span data-stu-id="f8665-156">It runs alongside each service and provides a platform-agnostic foundation for the following features:</span></span>

- <span data-ttu-id="f8665-157">Dynamické zjišťování služeb.</span><span class="sxs-lookup"><span data-stu-id="f8665-157">Dynamic service discovery.</span></span>
- <span data-ttu-id="f8665-158">Vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="f8665-158">Load balancing.</span></span>
- <span data-ttu-id="f8665-159">Ukončení protokolu TLS.</span><span class="sxs-lookup"><span data-stu-id="f8665-159">TLS termination.</span></span>
- <span data-ttu-id="f8665-160">Proxy servery HTTP a gRPC.</span><span class="sxs-lookup"><span data-stu-id="f8665-160">HTTP and gRPC proxies.</span></span>
- <span data-ttu-id="f8665-161">Odolnost přerušení okruhu.</span><span class="sxs-lookup"><span data-stu-id="f8665-161">Circuit breaker resiliency.</span></span>
- <span data-ttu-id="f8665-162">Kontroly stavu.</span><span class="sxs-lookup"><span data-stu-id="f8665-162">Health checks.</span></span>
- <span data-ttu-id="f8665-163">Aktualizace pro [Kanárské](https://martinfowler.com/bliki/CanaryRelease.html) nasazení.</span><span class="sxs-lookup"><span data-stu-id="f8665-163">Rolling updates with [canary](https://martinfowler.com/bliki/CanaryRelease.html) deployments.</span></span>

<span data-ttu-id="f8665-164">Jak je popsáno výše, zástupné se nasadí jako postranní vozík do každé mikroslužby v clusteru.</span><span class="sxs-lookup"><span data-stu-id="f8665-164">As previously discussed, Envoy is deployed as a sidecar to each microservice in the cluster.</span></span>

## <a name="integration-with-azure-kubernetes-services"></a><span data-ttu-id="f8665-165">Integrace se službami Azure Kubernetes</span><span class="sxs-lookup"><span data-stu-id="f8665-165">Integration with Azure Kubernetes Services</span></span>

<span data-ttu-id="f8665-166">Cloud Azure zahrnuje Istio a poskytuje přímou podporu pro IT v rámci služby Azure Kubernetes Services.</span><span class="sxs-lookup"><span data-stu-id="f8665-166">The Azure cloud embraces Istio and provides direct support for it within Azure Kubernetes Services.</span></span> <span data-ttu-id="f8665-167">Následující odkazy vám pomůžou začít:</span><span class="sxs-lookup"><span data-stu-id="f8665-167">The following links can help you get started:</span></span>

- [<span data-ttu-id="f8665-168">Instalace Istio v AKS</span><span class="sxs-lookup"><span data-stu-id="f8665-168">Installing Istio in AKS</span></span>](https://docs.microsoft.com/azure/aks/istio-install)
- [<span data-ttu-id="f8665-169">Použití AKS a Istio</span><span class="sxs-lookup"><span data-stu-id="f8665-169">Using AKS and Istio</span></span>](https://docs.microsoft.com/azure/aks/istio-scenario-routing)

### <a name="references"></a><span data-ttu-id="f8665-170">Odkazy</span><span class="sxs-lookup"><span data-stu-id="f8665-170">References</span></span>

- [<span data-ttu-id="f8665-171">Polly</span><span class="sxs-lookup"><span data-stu-id="f8665-171">Polly</span></span>](http://www.thepollyproject.org/)

- [<span data-ttu-id="f8665-172">Vzor opakování</span><span class="sxs-lookup"><span data-stu-id="f8665-172">Retry pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/retry)

- [<span data-ttu-id="f8665-173">Model Jistič (Circuit Breaker)</span><span class="sxs-lookup"><span data-stu-id="f8665-173">Circuit Breaker pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

- [<span data-ttu-id="f8665-174">Odolnost v Azure White Paper</span><span class="sxs-lookup"><span data-stu-id="f8665-174">Resilience in Azure whitepaper</span></span>](https://azure.microsoft.com/mediahandler/files/resourcefiles/resilience-in-azure-whitepaper/Resilience%20in%20Azure.pdf)

- [<span data-ttu-id="f8665-175">latence sítě</span><span class="sxs-lookup"><span data-stu-id="f8665-175">network latency</span></span>](https://www.techopedia.com/definition/8553/network-latency)

- [<span data-ttu-id="f8665-176">Redundance</span><span class="sxs-lookup"><span data-stu-id="f8665-176">Redundancy</span></span>](https://docs.microsoft.com/azure/architecture/guide/design-principles/redundancy)

- [<span data-ttu-id="f8665-177">geografická replikace</span><span class="sxs-lookup"><span data-stu-id="f8665-177">geo-replication</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication)

- [<span data-ttu-id="f8665-178">Traffic Manager Azure</span><span class="sxs-lookup"><span data-stu-id="f8665-178">Azure Traffic Manager</span></span>](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)

- [<span data-ttu-id="f8665-179">Pokyny k automatickému škálování</span><span class="sxs-lookup"><span data-stu-id="f8665-179">Autoscaling guidance</span></span>](https://docs.microsoft.com/azure/architecture/best-practices/auto-scaling)

- [<span data-ttu-id="f8665-180">Istio</span><span class="sxs-lookup"><span data-stu-id="f8665-180">Istio</span></span>](https://istio.io/docs/concepts/what-is-istio/)

- [<span data-ttu-id="f8665-181">Proxy zástupné</span><span class="sxs-lookup"><span data-stu-id="f8665-181">Envoy proxy</span></span>](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)

>[!div class="step-by-step"]
><span data-ttu-id="f8665-182">[Předchozí](infrastructure-resiliency-azure.md) 
> [Další](monitoring-health.md)</span><span class="sxs-lookup"><span data-stu-id="f8665-182">[Previous](infrastructure-resiliency-azure.md)
[Next](monitoring-health.md)</span></span>
