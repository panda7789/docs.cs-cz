---
title: "Strategie pro zpracování částečné selhání"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Strategie pro zpracování částečné selhání"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ff3bed530b13a9b1822c7cccf5a4d47df6fc6239
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="strategies-for-handling-partial-failure"></a>Strategie pro zpracování částečné selhání

Strategie pro práci s částečné selhání patří.

**Použít asynchronní komunikaci (například na základě zpráv) ve vnitřní mikroslužeb**. Se důrazně doporučuje není vytvoření dlouho řetězy synchronní volání protokolu HTTP mezi interní mikroslužeb vzhledem k tomu, že nesprávné návrhu nakonec bude hlavní příčinou chybný výpadků. Naopak, s výjimkou front-end komunikace mezi klientskými aplikacemi a první úroveň mikroslužeb nebo podrobných brány rozhraní API, doporučuje se použít jenom asynchronní (na základě zpráv) komunikaci jednou po počáteční žádosti nebo odpověď cyklus napříč interní mikroslužeb. Konzistence typu případné a událostmi řízené architektury pomůže omezit ripple účinky. Tyto přístupy vynutit na vyšší úrovni mikroslužbu nezávislé a proto zabránit proti problém, jsou tady uvedené.

**Pomocí opakování exponenciálního omezení rychlosti**. Tato technika pomáhá zamezit krátký a občasné chyby provedením volání opakování počet dobu, v případě, že služba nebyla k dispozici pouze po krátkou dobu. Mohlo to být kvůli problémům se sítí přerušované nebo mikroslužbu nebo kontejner je přesunut do jiného uzlu v clusteru. Pokud tyto opakování nejsou správně navržený s moduly dělení okruh, je však zhoršit ripple důsledky, nakonec i což způsobilo [útok na dostupnost služby (DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack).

**Práce mimo časové limity sítě**. Klienti musí být navrženy tak, není k blokování po neomezenou dobu a používat překročení časového limitu při čekání na odpověď. Použití časových limitů zajistí, že prostředky jsou nikdy svázané po neomezenou dobu.

**Použití vzoru jistič**. V tomto přístupu procesu klienta sleduje počet neúspěšných požadavků. Pokud je míra chyb překračuje limit konfiguraci cest "jistič" tak, aby další pokusy o neúspěšné okamžitě. (Pokud se nedaří velký počet požadavků, která během psaní navrhuje služba není dostupná a že je zbytečný odesílání požadavků.) Po uplynutí doby vypršení časového limitu klienta by měl zkuste to znovu a, pokud jsou úspěšné, nové požadavky zavřete vypínač.

**Zadejte případech Přejít**. V tento přístup procesu klienta provede záložní Pokud se požadavek nezdaří, jako je například vrací data uložená v mezipaměti nebo výchozí hodnotu. Toto je vhodný pro dotazy přístup a složitější pro aktualizace nebo příkazy.

**Omezit počet požadavků ve frontě**. Klienti musí také jiné než horní mez počtu nevyřízených požadavků, které mikroslužbu klient může odesílat do konkrétní služby. Pokud bylo dosaženo limitu, je pravděpodobně neúčinná provádět další požadavky a těmito pokusy má okamžitě selhat. Z hlediska implementace, Polly [přepážkovou izolace](https://github.com/App-vNext/Polly/wiki/Bulkhead) zásadu lze použít ke splnění tohoto požadavku. Tento přístup je v podstatě paralelizace omezení s [SemaphoreSlim](https://docs.microsoft.com/dotnet/api/system.threading.semaphoreslim?view=netcore-1.1) jako implementace. Token taky umožňuje "fronty" mimo přepážka. Můžete proaktivně přenesen nadbytečné zatížení i před spuštěním, (například proto kapacity se považuje úplná). Díky tomu odpovědi na určité scénáře selhání rychleji, než by bylo jistič, protože čeká jistič selhání. Objekt BulkheadPolicy v Polly zpřístupňuje jak úplné přepážkovou a jsou fronty a nabízí události přetečení tak mohou sloužit také k řízení automatizované vodorovné škálování.

## <a name="additional-resources"></a>Další zdroje

-   **Odolnost proti chybám vzory**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Přidání odolnost a optimalizace výkonu**
    [*https://msdn.microsoft.com/en-us/library/jj591574.aspx*](https://msdn.microsoft.com/en-us/library/jj591574.aspx)

-   **Přepážkovou.** Úložiště GitHub. Implementace zásadám Polly. \
    [*https://github.com/App-vNext/Polly/Wiki/Bulkhead*](https://github.com/App-vNext/Polly/wiki/Bulkhead)

-   **Návrh odolný aplikací pro Azure**
    [*https://docs.microsoft.com/azure/architecture/resiliency/*](https://docs.microsoft.com/azure/architecture/resiliency/)

-   **Přechodná chyba zpracování**
    <https://docs.microsoft.com/azure/architecture/best-practices/transient-faults>


>[!div class="step-by-step"]
[Předchozí] (popisovač partial-failure.md) [Další] (implementace opakování exponenciální backoff.md)
