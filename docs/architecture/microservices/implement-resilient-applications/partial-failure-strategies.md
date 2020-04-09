---
title: Strategie pro zpracování částečného selhání
description: Seznamte se s několika strategiemi pro řádné zpracování částečných chyb.
ms.date: 10/16/2018
ms.openlocfilehash: abf87df5afed02b4d794a1307a0ed943cafb4db3
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988801"
---
# <a name="strategies-to-handle-partial-failure"></a>Strategie pro zpracování částečného selhání

Strategie pro řešení částečných selhání zahrnují následující.

**Používejte asynchronní komunikaci (například komunikaci založenou na zprávě) mezi interními mikroslužbami**. Je velmi vhodné nevytvářet dlouhé řetězce synchronní volání HTTP napříč interní mikroslužeb, protože tento nesprávný návrh se nakonec stane hlavní příčinou výpadků chyb. Naopak, s výjimkou front-endové komunikace mezi klientskými aplikacemi a první úrovní mikroslužeb nebo jemně odstupňovaných bran rozhraní API se doporučuje používat pouze asynchronní (na základě zpráv) komunikaci po počátečním cyklu požadavku a odpovědi napříč interními mikroslužbami. Konečná konzistence a architektury řízené událostmi pomohou minimalizovat dominové efekty. Tyto přístupy vynucují vyšší úroveň autonomie mikroslužeb a proto zabraňují problému, který je zde uveden.

**Použijte opakované pokusy s exponenciálním zpětným vypnutím**. Tato technika pomáhá vyhnout se krátkým a přerušovaným chybám provedením opakovaných pokusů o volání určitý počet opakování v případě, že služba nebyla k dispozici pouze krátkou dobu. K tomu může dojít z důvodu občasné problémy se sítí nebo při mikroslužeb nebo kontejner je přesunuta do jiného uzlu v clusteru. Pokud však tyto opakování nejsou správně navrženy s jističi, může zhoršit dominové efekty, což nakonec dokonce způsobí [odmítnutí služby (DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack).

**Obejít časové očasové časové opony sítě**. Obecně by klienti měli být navrženi tak, aby neblokovali neomezeně dlouho a vždy používali časové osy při čekání na odpověď. Použití časových časových opovenek zajišťuje, že prostředky nejsou nikdy vázány na neurčito.

**Použijte vzor jističe**. V tomto přístupu proces u klienta sleduje počet neúspěšných požadavků. Pokud chybovost překročí nakonfigurovaný limit, "jistič" zakopne tak, aby další pokusy okamžitě selhaly. (Pokud velký počet požadavků selhávají, to naznačuje, že služba není k dispozici a že odesílání požadavků je zbytečné.) Po uplynutí časového období by měl klient zkusit znovu a pokud jsou nové požadavky úspěšné, zavřete jistič.

**Poskytněte záložní soubory**. V tomto přístupu klientský proces provádí záložní logiku při selhání požadavku, jako je například vrácení dat v mezipaměti nebo výchozí hodnota. Jedná se o přístup vhodný pro dotazy a je složitější pro aktualizace nebo příkazy.

**Omezte počet požadavků zařazených do fronty**. Klienti by také měli uložit horní mez počtu nevyřízených požadavků, které může mikroslužba klienta odeslat určité službě. Pokud bylo dosaženo limitu, je pravděpodobně zbytečné provádět další požadavky a tyto pokusy by měly okamžitě selhat. Z hlediska implementace polly [přepážka izolace](https://github.com/App-vNext/Polly/wiki/Bulkhead) zásady lze použít ke splnění tohoto požadavku. Tento přístup je v podstatě omezení paralelizace s <xref:System.Threading.SemaphoreSlim> jako implementace. Umožňuje také "frontu" mimo přepážku. Můžete proaktivně zbavit nadměrné zatížení ještě před spuštěním (například proto, že kapacita je považována za plnou). Díky tomu je jeho reakce na určité scénáře selhání rychlejší, než by byl jistič, protože jistič čeká na poruchy. BulkheadPolicy objekt u [Polly](http://www.thepollyproject.org/) zveřejňuje, jak plná přepážka a fronty jsou a nabízí události na přetečení, takže lze také použít k řízení automatické horizontální škálování.

## <a name="additional-resources"></a>Další zdroje

- **Vzory odolnosti proti chybám**\
  [https://docs.microsoft.com/azure/architecture/patterns/category/resiliency](/azure/architecture/patterns/category/resiliency)

- **Přidání odolnosti a optimalizace výkonu**\
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591574(v=pandp.10)>

- **Přepážky.** úložiště GitHub. Implementace s polly politikou.\
  <https://github.com/App-vNext/Polly/wiki/Bulkhead>

- **Navrhování odolných aplikací pro Azure**\
  [https://docs.microsoft.com/azure/architecture/resiliency/](/azure/architecture/resiliency/)

- **Přechodná manipulace s poruchami**\
  [https://docs.microsoft.com/azure/architecture/best-practices/transient-faults](/azure/architecture/best-practices/transient-faults)

>[!div class="step-by-step"]
>[Předchozí](handle-partial-failure.md)
>[další](implement-retries-exponential-backoff.md)
