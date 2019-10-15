---
title: Odolná komunikace
description: Architekt cloudových nativních aplikací .NET pro Azure | Odolná komunikace
ms.date: 06/30/2019
ms.openlocfilehash: 324f5426af1c892db73aa6fc2336a19b7a8e499e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315801"
---
# <a name="resilient-communications"></a>Odolná komunikace

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

V rámci této knihy jsme evangelizedi, že se přesouvají mimo tradiční návrh aplikací monolitické a přechodu architekturu založenou na mikroslužbách, kde se sada distribuovaných a samoobslužných služeb spouští nezávisle a komunikuje s nimi. jiné pomocí standardních komunikačních protokolů, jako jsou HTTP a HTTPS. I když taková architektura koupí mnoho důležitých výhod, prezentuje i mnoho výzev. Vezměte v úvahu například následující aspekty:

- *Neprocesová síťová komunikace.* Každá služba komunikuje přes síťový protokol, který zavádí zahlcení sítě, latenci a přechodné chyby.
- *Zjišťování služby.* U každé služby spuštěné v clusteru počítačů s vlastní IP adresou a portem jak služby navzájem zjišťují a komunikují?
- *Odolnost.* Jak se spravují krátkodobé nenáročné chyby a systém udržuje stabilní?
- *Vyrovnávání zatížení.* Jak se příchozí provoz rozděluje mezi více instancí služby?
- *Bezpečnost.* Jak se týká zabezpečení, jako je šifrování na úrovni přenosu a Správa certifikátů?
- *Distribuované monitorování.* – Jak korelujete a zachytíte sledovatelnost a monitorování pro jednotlivé požadavky v rámci více využívání služeb?

I když tyto otázky lze řešit pomocí různých knihoven a architektur, jejich implementace v rámci základu kódu mohou být nákladné, komplexní a časově náročné. Kromě toho se ukončí řešení, ve kterém souvisí infrastruktura infrastruktury s obchodní logikou.

## <a name="service-mesh"></a>Síť sítě

Lepším řešením je uvažovat o nové a rychle se rozvíjející se technologie s názvem *sítě*. [Síť](https://www.nginx.com/blog/what-is-a-service-mesh/) je konfigurovatelná vrstva infrastruktury s integrovanými možnostmi pro zpracování komunikace služby a mnohé z výše uvedených výzev. Odděluje tyto obavy z vašeho podnikového kódu a přesouvá je do proxy služby, instance, která doprovází každou z vašich služeb. Pro zajištění izolace a zapouzdření z vašeho podnikového kódu se často označuje jako [vzorek postranního vozíku](https://docs.microsoft.com/azure/architecture/patterns/sidecar). proxy síť služby se nasadí do samostatného procesu. Proxy server se ale úzce odkazuje na službu, která se vytváří společně s IT a sdílí životní cyklus. Obrázek 6-9 ukazuje tento scénář.

![Síť s postranním vozíkem](./media/service-mesh-with-side-car.png)

**Obrázek 6-9**. Síť s postranním vozíkem

Na předchozím obrázku si všimněte, jak proxy zachytí a spravuje komunikaci mezi mikroslužbami a clusterem.

Síť je logicky rozdělená na dvě různorodé komponenty: [rovina dat](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) a [rovina ovládacího prvku](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc). Obrázek 6-10 ukazuje tyto komponenty a jejich zodpovědnosti.

![Ovládací prvek sítě a rovina dat](./media/istio-control-and-data-plane.png)

**Obrázek 6-10.** Ovládací prvek sítě a rovina dat

Po nakonfigurování je síť velmi funkční. Může načíst odpovídající fond instancí z koncového bodu zjišťování služby. Pak může odeslat požadavek na konkrétní instanci a zaznamenat latenci a typ odpovědi výsledku. Síť může zvolit instanci, která pravděpodobně vrátí rychlou odpověď na základě mnoha faktorů, včetně pozorované latence pro poslední požadavky.

Pokud instance nereaguje nebo se nezdařila, síť může opakovat požadavek na jinou instanci. Pokud fond konzistentně vrátí chyby, síť ho může vyřadit z fondu vyrovnávání zatížení, aby bylo možné je pravidelně opakovat později po tom, co je zamění. Pokud vyprší časový limit požadavku, může dojít k selhání sítě a pak požadavek opakujte. Mřížka zachycuje chování ve formě metrik a distribuovaného trasování, které pak lze vygenerovat do centralizovaného systému metrik.

## <a name="istio-and-envoy"></a>Istio a zástupné

I když existuje několik možností sítě, které jsou aktuálně k dispozici, [Istio](https://istio.io/docs/concepts/what-is-istio/) je nejoblíbenější k době psaní. Společný podnik od IBM, Google a Lyft je open source nabídka, kterou je možné integrovat do nové nebo stávající distribuované aplikace. Poskytuje konzistentní a kompletní řešení pro zabezpečení, připojení a monitorování mikroslužeb. Mezi tyto funkce patří:

- Zabezpečená komunikace mezi službami v clusteru se silným ověřováním a autorizací na základě identity.
- Automatické vyrovnávání zatížení pro přenosy HTTP, [gRPC](https://grpc.io/), WebSocket a TCP.
- Jemně odstupňovaná kontrola nad chováním provozu s bohatými pravidly směrování, opakovanými pokusy, převzetí služeb při selhání a vkládáním chyb.
- Připojitelná vrstva zásad a konfigurační rozhraní API, které podporuje řízení přístupu, omezení přenosové rychlosti a kvóty.
- Automatické metriky, protokoly a trasování pro veškerý provoz v rámci clusteru, včetně příchozího a odchozího clusteru.

Klíčovou komponentou pro implementaci Istio je proxy služba s oprávněním [proxy serveru zástupné](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy). Pocházející z Lyft a následně přispěly ke [Cloud Native Computing Foundation](https://www.cncf.io/) (popsaný v kapitole 1) se proxy zástupné spouští spolu s každou službou a poskytuje platformu-nezávislá Foundation pro následující funkce:

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

>[!div class="step-by-step"]
>[Předchozí](infrastructure-resiliency-azure.md)
>[Další](monitoring-health.md)
