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
# <a name="resilient-communications"></a>Odolná komunikace

V celé této příručce jsme dělali přístup k architektuře založené na mikroslužbách. I když taková architektura přináší důležité výhody, představuje mnoho výzev:

- *Neprocesová síťová komunikace.* Každá mikroslužba komunikuje přes síťový protokol, který zavádí zahlcení sítě, latenci a přechodné chyby.

- *Zjišťování služby.* Jak mikroslužby zjišťují a vzájemně komunikují při provozu v clusteru počítačů s vlastními IP adresami a porty?

- *Odolnost.* Jak se spravují krátkodobé nenáročné chyby a systém udržuje stabilní?

- *Vyrovnávání zatížení.* Jak se příchozí provoz rozděluje napříč víc instancemi mikroslužeb?

- *Bezpečnost.* Jak se týká zabezpečení, jako je šifrování na úrovni přenosu a Správa certifikátů?

- *Distribuované monitorování.* – Jak korelujete a zachytíte sledovatelnost a monitorování pro jeden požadavek napříč několika náročnými mikroslužbami?

Tyto aspekty můžete vyřešit pomocí různých knihoven a architektur, ale implementace může být náročná, složitá a časově náročná. I když máte i nadále problémy s infrastrukturou, která je spojená s obchodní logikou.

## <a name="service-mesh"></a>Síť sítě

Lepším přístupem je vyvíjející se technologie s názvem *sítě*. [Síť](https://www.nginx.com/blog/what-is-a-service-mesh/) je konfigurovatelná vrstva infrastruktury s integrovanými možnostmi pro zpracování komunikace služby a dalších výzev uvedených výše. Tyto otázky se oddělí přesunutím na proxy služby. Proxy server se nasadí do samostatného procesu (označovaného jako [postranní vozík](https://docs.microsoft.com/azure/architecture/patterns/sidecar)), aby poskytoval izolaci od obchodního kódu. Tento postranní vozík je ale spojený s touto službou – vytvoří se s ním a sdílí životní cyklus. Obrázek 6-7 ukazuje tento scénář.

![Síť s postranním vozíkem](./media/service-mesh-with-side-car.png)

**Obrázek 6-7**. Síť s postranním vozíkem

Na předchozím obrázku si všimněte, jak proxy zachytí a spravuje komunikaci mezi mikroslužbami a clusterem.

Síť je logicky rozdělená na dvě různorodé komponenty: [rovina dat](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) a [rovina ovládacího prvku](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc). Obrázek 6-8 ukazuje tyto komponenty a jejich zodpovědnosti.

![Ovládací prvek sítě a rovina dat](./media/istio-control-and-data-plane.png)

**Obrázek 6-8.** Ovládací prvek sítě a rovina dat

Po nakonfigurování je síť velmi funkční. Může načíst odpovídající fond instancí z koncového bodu zjišťování služby. Síť pak může poslat požadavek na konkrétní instanci, která zaznamená latenci a typ odpovědi výsledku. Síť může zvolit instanci, která pravděpodobně vrátí rychlou odpověď na základě mnoha faktorů, včetně pozorované latence pro poslední požadavky.

Pokud instance nereaguje nebo se nezdaří, síť zopakuje požadavek na jiné instanci. Pokud dojde k chybám, síť vyřadí instanci z fondu vyrovnávání zatížení a po tom, co je zavede, ji obnoví. Pokud vyprší časový limit požadavku, může dojít k selhání sítě a pak požadavek opakujte. Síť vychytí a vysílá metriky a distribuované trasování do centralizovaného systému metrik.

## <a name="istio-and-envoy"></a>Istio a zástupné

I když existuje několik možností sítě, které aktuálně existují, [Istio](https://istio.io/docs/concepts/what-is-istio/) je nejoblíbenější v době psaní tohoto textu. Istio je společný podnik od IBM, Google a Lyft. Jedná se o open-source nabídku, kterou je možné integrovat do nové nebo stávající distribuované aplikace. Technologie poskytuje konzistentní a kompletní řešení pro zabezpečení, připojení a monitorování mikroslužeb. Mezi tyto funkce patří:

- Zabezpečená komunikace mezi službami v clusteru se silným ověřováním a autorizací na základě identity.
- Automatické vyrovnávání zatížení pro přenosy HTTP, [gRPC](https://grpc.io/), WebSocket a TCP.
- Jemně odstupňovaná kontrola nad chováním provozu s bohatými pravidly směrování, opakovanými pokusy, převzetí služeb při selhání a vkládáním chyb.
- Připojitelná vrstva zásad a konfigurační rozhraní API, které podporuje řízení přístupu, omezení přenosové rychlosti a kvóty.
- Automatické metriky, protokoly a trasování pro veškerý provoz v rámci clusteru, včetně příchozího a odchozího clusteru.

Klíčovou komponentou pro implementaci Istio je proxy služba s oprávněním [proxy serveru zástupné](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy). Spouští se spolu se všemi službami a poskytuje platformu nezávislá Foundation pro následující funkce:

- Dynamické zjišťování služeb.
- Vyrovnávání zatížení.
- Ukončení protokolu TLS.
- Proxy servery HTTP a gRPC.
- Odolnost přerušení okruhu.
- Kontroly stavu.
- Aktualizace pro [Kanárské](https://martinfowler.com/bliki/CanaryRelease.html) nasazení.

Jak je popsáno výše, zástupné se nasadí jako postranní vozík do každé mikroslužby v clusteru.

## <a name="integration-with-azure-kubernetes-services"></a>Integrace se službami Azure Kubernetes

Cloud Azure zahrnuje Istio a poskytuje přímou podporu pro IT v rámci služby Azure Kubernetes Services. Následující odkazy vám pomůžou začít:

- [Instalace Istio v AKS](https://docs.microsoft.com/azure/aks/istio-install)
- [Použití AKS a Istio](https://docs.microsoft.com/azure/aks/istio-scenario-routing)

### <a name="references"></a>Odkazy

- [Polly](http://www.thepollyproject.org/)

- [Vzor opakování](https://docs.microsoft.com/azure/architecture/patterns/retry)

- [Model Jistič (Circuit Breaker)](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

- [Odolnost v Azure White Paper](https://azure.microsoft.com/mediahandler/files/resourcefiles/resilience-in-azure-whitepaper/Resilience%20in%20Azure.pdf)

- [latence sítě](https://www.techopedia.com/definition/8553/network-latency)

- [Redundance](https://docs.microsoft.com/azure/architecture/guide/design-principles/redundancy)

- [geografická replikace](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication)

- [Traffic Manager Azure](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)

- [Pokyny k automatickému škálování](https://docs.microsoft.com/azure/architecture/best-practices/auto-scaling)

- [Istio](https://istio.io/docs/concepts/what-is-istio/)

- [Proxy zástupné](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)

>[!div class="step-by-step"]
>[Předchozí](infrastructure-resiliency-azure.md) 
> [Další](monitoring-health.md)
