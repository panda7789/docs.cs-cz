---
title: Strategie pro zpracování částečného selhání
description: Seznamte se několik strategií pro zpracování částečného selhání bez výpadku.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 63c6764d18ee0a8990cf669a8cdc824dea79aac8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020164"
---
# <a name="strategies-to-handle-partial-failure"></a>Strategie pro zpracování částečného selhání

Strategie pro práci s částečně neúspěšné patří.

**Použít asynchronní komunikaci (například založenou na zprávách) napříč interní mikroslužeb**. Se důrazně doporučuje nechcete vytvořit dlouhé řetězce o synchronních voláních HTTP mezi interní mikroslužeb, protože tento nesprávné návrhu se nakonec stanou hlavní příčinou chybný výpadků. Naopak, s výjimkou front-endu komunikace mezi klientskými aplikacemi a první úroveň z mikroslužeb nebo jemné brány rozhraní API, doporučujeme používat pouze asynchronní (založená na zprávách) jednou za počáteční požadavek / cyklus odezvy mezi interní mikroslužeb. Konečné konzistence a architektury řízené událostmi pomůže omezit ripple účinky. Tyto přístupy vynutit vyšší úroveň autonomie mikroslužeb a zabránit tak před problémem jsou tady uvedené.

**Opakování pomocí exponenciálního omezení rychlosti**. Tento přístup umožňuje vyhnout se krátký a občasné chyby pomocí provádí volání opakování s určitým počtem opakování, v případě, že služba nebyla k dispozici pouze krátkou dobu. Tato situace může nastat kvůli problémům s sítě nebo mikroslužeb a kontejnerů se přesune do jiného uzlu v clusteru. Ale pokud tyto opakování nejsou správně navržená se jističe a to zhoršit ripple účinky, takže v konečném důsledku i způsobující [útok na dostupnost služby (DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack).

**Alternativní vypršení časového limitu sítě**. Obecně platí klienti by se měly navrhovat blokovaná a používat vypršení časového limitu při čekání na odpověď. Použití časových limitů zajistí, že prostředky nikdy svázané s po neomezenou dobu.

**Použití vzoru Circuit Breaker**. V takovém případě proces klienta sleduje počet neúspěšných žádostí. Pokud chybovost překročí nakonfigurovaný limit "jistič" cesty tak, aby další pokusy selhala okamžitě. (Pokud se nedaří velký počet požadavků, návrhy služby není k dispozici a že je zbytečný odesílání požadavků.) Po uplynutí časového limitu klienta by měl zkuste to znovu a pokud jsou úspěšné, nové požadavky zavřít jistič.

**Zadejte náhrad**. V takovém případě proces klienta provede náhradní logiku, když bude žádost neúspěšná, jako je vracení dat uložených v mezipaměti nebo výchozí hodnotu. To je vhodný pro dotazy, přístup a je složitější aktualizací nebo příkazy.

**Omezení počtu požadavků zařazených do fronty**. Klienti musí také ukládat horní mez počtu nevyřízených požadavků klienta mikroslužby mohou odesílat do konkrétní služby. Pokud bylo dosaženo limitu, je pravděpodobně bezúčelné další požadavky a těchto pokusů musí selhat, okamžitě. Z hlediska implementace, Polly [přepážka izolace](https://github.com/App-vNext/Polly/wiki/Bulkhead) zásadu lze použít ke splnění tohoto požadavku. Tento přístup je v podstatě paralelizace omezení s <xref:System.Threading.SemaphoreSlim> jako implementace. Umožňuje také "fronty" mimo přepážky. Můžete aktivně zbavit nadměrné zatížení ještě před spuštěním (například proto kapacity se bude považovat za úplné). Díky tomu odpověď určitých scénářích selhání rychleji, než by jistič, protože jistič čeká na chyby. Objekt BulkheadPolicy v [Polly](http://www.thepollyproject.org/) jsou zpřístupňuje jak úplné přepážka a fronty a nabídky události při přetečení tak můžete také použít Centrum umožňující prosazovat automatické horizontální škálování.

## <a name="additional-resources"></a>Další zdroje

- **Způsoby zajištění odolnosti**\
  [https://docs.microsoft.com/azure/architecture/patterns/category/resiliency](/azure/architecture/patterns/category/resiliency)

- **Přidání odolnost a optimalizace výkonu**\
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591574(v=pandp.10)>

- **Bulkhead.** Úložiště GitHub. Implementace pomocí knihovny Polly zásad. \
  <https://github.com/App-vNext/Polly/wiki/Bulkhead>

- **Návrh odolných aplikací pro Azure**\
  [https://docs.microsoft.com/azure/architecture/resiliency/](/azure/architecture/resiliency/)

- **Zpracování přechodných chyb**\
  [https://docs.microsoft.com/azure/architecture/best-practices/transient-faults](/azure/architecture/best-practices/transient-faults)

>[!div class="step-by-step"]
>[Předchozí](handle-partial-failure.md)
>[další](implement-retries-exponential-backoff.md)
