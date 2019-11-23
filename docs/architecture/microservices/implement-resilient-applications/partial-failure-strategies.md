---
title: Strategie pro zpracování částečného selhání
description: Získejte informace o několika strategiích pro řádné zpracování částečných selhání.
ms.date: 10/16/2018
ms.openlocfilehash: e96fe99ab44b924460e01abaad30aa3e2432117a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296047"
---
# <a name="strategies-to-handle-partial-failure"></a>Strategie pro zpracování částečného selhání

Mezi strategie týkající se práce s částečnými chybami patří následující.

**Použijte asynchronní komunikaci (například komunikaci založenou na zprávách) napříč interními mikroslužbami**. Je velmi vhodné nevytvářet dlouhé řetězce synchronních volání HTTP napříč interními mikroslužbami, protože tento nesprávný návrh se nakonec stane hlavní příčinou špatných výpadků. V opačném případě, s výjimkou front-endové komunikace mezi klientskými aplikacemi a první úrovní mikroslužeb nebo jemně odstupňovaných bran rozhraní API, se doporučuje použít pouze asynchronní komunikaci (založenou na zprávách) po předchozím cyklu požadavku a odpovědi v rámci interních mikroslužeb. Konečné architektury a architektury založené na událostech vám pomůžou minimalizovat efekty Ripple. Tyto přístupy vynutily vyšší úroveň autonomie mikroslužeb, a proto zabrání před problémem, který je zde popsán.

**Použijte opakování s exponenciálním omezení rychlosti**. Tato technika pomáhá vyhnout se krátkým a přerušovaným selháním, protože provádí volání opakované pokusy v případě, že služba nebyla k dispozici pouze po krátkou dobu. Tato situace může nastat kvůli přerušovaným problémům se sítí nebo při přesunu mikroslužby/kontejneru do jiného uzlu v clusteru. Pokud se ale tyto pokusy nenavrhují správně s vypínači okruhu, může to zhoršit efekty v Ripple a nakonec způsobit [odepření služby (DOS)](https://en.wikipedia.org/wiki/Denial-of-service_attack).

**Obejít časovým limitům sítě**. Obecně platí, že klienti by měli být navrženi tak, aby neblokovali neomezenou dobu a při čekání na odpověď vždy používali časové limity. Použití časových limitů zajistí, že se prostředky nikdy neúčtují po neomezenou dobu.

**Použijte vzorek pro přerušení okruhu**. V tomto přístupu proces klienta sleduje počet neúspěšných žádostí. Pokud míra chyb překročí nakonfigurovaný limit, "přepínací modul okruhu", aby se další pokusy navzájem nezdařily okamžitě. (Pokud se nedaří velký počet požadavků, která naznačuje, že služba není k dispozici a že odeslání požadavků je bezúčelné.) Po uplynutí časového limitu se klient může pokusit znovu, a pokud jsou nové požadavky úspěšné, uzavřete okruh okruhů.

**Poskytněte záložní**verze. V tomto přístupu proces klienta provádí záložní logiku, když požadavek selhává, jako je například vrácení dat do mezipaměti nebo výchozí hodnota. Toto je přístup vhodný pro dotazy a je složitější pro aktualizace nebo příkazy.

**Omezte počet požadavků zařazených do fronty**. Klienti by také měli mít horní mez počtu nezpracovaných požadavků, které může klientská služba odeslat do konkrétní služby. Pokud se dosáhlo limitu, je pravděpodobné, že je bezúčelné udělat další požadavky a tyto pokusy by se okamžitě měly zdařit. V souvislosti s implementací je možné k splnění tohoto požadavku použít zásady [izolace Polly přepážek](https://github.com/App-vNext/Polly/wiki/Bulkhead) . Tento přístup je v podstatě omezení paralelismu s <xref:System.Threading.SemaphoreSlim> jako implementace. Povoluje také "frontu" mimo přepážku. Můžete proaktivně uvolnit nadměrné zatížení dokonce ještě před provedením (například kvůli tomu, že kapacita je považována za plná). Díky tomu bude odpověď na určité scénáře selhání rychlejší než přepínací modul okruhů, protože přepínací modul okruhů čeká na selhání. Objekt BulkheadPolicy v [Polly](http://www.thepollyproject.org/) vystavuje, jak plná přepážka a fronta je, a nabízí události přetečení, takže je možné také použít k automatickému horizontálnímu škálování.

## <a name="additional-resources"></a>Další materiály a zdroje informací

- \ **vzory odolnosti**
  [https://docs.microsoft.com/azure/architecture/patterns/category/resiliency](/azure/architecture/patterns/category/resiliency)

- **Přidání odolnosti a optimalizace\ výkonu**
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591574(v=pandp.10)>

- **Bulkhead.** Úložiště GitHub. Implementace pomocí zásad Polly \
  <https://github.com/App-vNext/Polly/wiki/Bulkhead>

- **Navrhování odolných aplikací pro Azure**\
  [https://docs.microsoft.com/azure/architecture/resiliency/](/azure/architecture/resiliency/)

- \ **zpracování přechodných chyb**
  [https://docs.microsoft.com/azure/architecture/best-practices/transient-faults](/azure/architecture/best-practices/transient-faults)

>[!div class="step-by-step"]
>[Předchozí](handle-partial-failure.md)
>[Další](implement-retries-exponential-backoff.md)
