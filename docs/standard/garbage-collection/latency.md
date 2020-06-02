---
title: Latentní režimy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: ee45fe5e8016c7507bc3a873e615fd8379810a8e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286012"
---
# <a name="latency-modes"></a>Režimy latence

Chcete-li uvolnit objekty, musí uvolňování paměti (GC) zastavit všechny spuštěné vlákna v aplikaci. Doba, během které je systém uvolňování paměti aktivní, se označuje jako *latence*.

V některých situacích, například když aplikace načítá data nebo zobrazuje obsah, může v kritickém čase dojít k úplnému uvolňování paměti a brání se tak výkonu. Můžete upravit rušivý systém uvolňování paměti nastavením <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> vlastnosti na jednu z <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> hodnot.

## <a name="low-latency-settings"></a>Nastavení nízké latence

Když použijete nastavení latence nízká, znamená to, že systém uvolňování paměti intrudes méně ve vaší aplikaci. Uvolňování paměti je více konzervativní pro uvolnění paměti.

<xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>Výčet poskytuje dvě nastavení s nízkou latencí:

- [GCLatencyMode. LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) potlačí kolekce 2. generace a provede pouze kolekce generace 0 a 1. Dá se použít jenom pro krátkou dobu. V delší dobu, pokud je systém v paměti, uvolňování paměti spustí kolekci, která může krátce pozastavit aplikaci a rušit kritické operace. Toto nastavení je dostupné jenom pro uvolňování paměti pracovní stanice.

- [GCLatencyMode. SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) potlačí kolekce na popředí 2. generace a provede pouze kolekce generace 0, 1 a Background generace 2. Dá se použít po delší dobu a je k dispozici pro pracovní stanici i pro uvolňování paměti serveru. Toto nastavení se nedá použít, pokud je zakázané uvolňování paměti na pozadí.

Během období s nízkou latencí jsou kolekce 2. generace potlačeny, pokud nedojde k následujícím akcím:

- Systém obdrží oznámení o nedostatku paměti z operačního systému.

- Kód aplikace vyvolá kolekci voláním <xref:System.GC.Collect%2A?displayProperty=nameWithType> metody a zadáním 2 pro `generation` parametr.

## <a name="scenarios"></a>Scénáře

Následující tabulka obsahuje seznam scénářů aplikací pro použití <xref:System.Runtime.GCLatencyMode> hodnot:

|Režim latence|Scénáře aplikací|
|------------------|---------------------------|
|<xref:System.Runtime.GCLatencyMode.Batch>|Pro aplikace, které nemají žádné uživatelské rozhraní (UI) nebo serverové operace.<br /><br />Když je zakázané uvolňování paměti na pozadí, jedná se o výchozí režim pro uvolnění paměti pracovní stanice a serveru. <xref:System.Runtime.GCLatencyMode.Batch>režim také přepisuje nastavení [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) , to znamená, že zabrání na pozadí nebo souběžných kolekcích.|
|<xref:System.Runtime.GCLatencyMode.Interactive>|Pro většinu aplikací, které mají uživatelské rozhraní.<br /><br />Toto je výchozí režim pro uvolňování paměti pracovních stanic a serverů. Pokud je však aplikace hostována, má přednost nastavení systému uvolňování paměti hostitelského procesu.|
|<xref:System.Runtime.GCLatencyMode.LowLatency>|Pro aplikace, které mají krátkodobé, časově citlivé operace, během kterých by mohlo dojít k přerušení výpadků ze systému uvolňování paměti. Například aplikace, které vykreslují animace nebo funkce pro získání dat.|
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|Pro aplikace, které mají časově náročné operace pro obsaženou, ale potenciálně delší dobu, kdy může dojít k přerušení výpadků ze systému uvolňování paměti. Například aplikace, které vyžadují dobu trvání rychlé odezvy v době, kdy se mění data trhu během doby obchodování.<br /><br />Výsledkem tohoto režimu je větší spravovaná velikost haldy než jiné režimy. Vzhledem k tomu, že nástroj nekomprimuje spravovanou haldu, je možné zvýšit fragmentaci. Ujistěte se, že je k dispozici dostatek paměti.|

## <a name="guidelines-for-using-low-latency"></a>Pokyny pro použití nízké latence

Při použití režimu [GCLatencyMode. LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) zvažte následující pokyny:

- Udržujte dobu v nízké latenci, která je co nejkratší.

- Vyhněte se přidělování vysoké velikosti paměti během období s nízkou latencí. K oznamování nedostatku paměti může dojít, protože uvolňování paměti uvolňuje méně objektů.

- V režimu s nízkou latencí Minimalizujte počet nových přidělení, zejména přidělení na haldu velkých objektů a připnuté objekty.

- Upozorňujeme na vlákna, která by se dala přidělit. Vzhledem k tomu <xref:System.Runtime.GCSettings.LatencyMode%2A> , že nastavení vlastnosti je v rámci procesu, <xref:System.OutOfMemoryException> lze výjimky generovat v jakémkoli vlákně, které je alokováno.

- Zabalte kód nízké latence v oblastech omezeného provádění. Další informace najdete v tématu [omezené oblasti provádění](../../framework/performance/constrained-execution-regions.md).

- Můžete vynutit generace 2 kolekce během období s nízkou latencí voláním <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> metody.

## <a name="see-also"></a>Viz také

- <xref:System.GC?displayProperty=nameWithType>
- [Vyvolané kolekce](induced.md)
- [Uvolňování paměti](index.md)
