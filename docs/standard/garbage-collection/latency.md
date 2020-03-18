---
title: Latentní režimy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: a8eaf0c80aa32978eead80c51a905cbcd66a537b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74283598"
---
# <a name="latency-modes"></a>Režimy latence

Chcete-li získat objekty, systém uvolňování paměti (GC) musí zastavit všechna spuštěná vlákna v aplikaci. Doba, po kterou je aktivní systém uvolňování paměti, se označuje jako jeho *latence*.

V některých situacích, například když aplikace načte data nebo zobrazí obsah, úplné uvolnění paměti může dojít v kritickém čase a bránit výkonu. Můžete upravit rušivost systému uvolňování paměti <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> nastavením vlastnosti <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> na jednu z hodnot.

## <a name="low-latency-settings"></a>Nastavení s nízkou latencí

Použití "nízké" latence nastavení znamená, že uvolňování vnikne méně ve vaší aplikaci. Uvolňování paměti je konzervativnější o uvolnění paměti.

Výčet <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> poskytuje dvě nastavení s nízkou latencí:

- [GCLatencyMode.LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) potlačuje kolekce generace 2 a provádí pouze generování 0 a 1 kolekce. Může být použit pouze na krátkou dobu. Po delší dobu, pokud je systém pod tlakem paměti, systém uvolňování paměti spustí kolekci, která může krátce pozastavit aplikaci a narušit časově kritickou operaci. Toto nastavení je k dispozici pouze pro uvolňování paměti pracovní stanice.

- [GCLatencyMode.SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) potlačuje kolekce generace popředí 2 a provádí pouze generování 0, 1 a pozadí generace 2 kolekce. Může být použit pro delší časové období a je k dispozici pro pracovní stanice a server uvolňování paměti. Toto nastavení nelze použít, pokud je zakázáno uvolňování paměti na pozadí.

Během období s nízkou latencí generace 2 kolekce jsou potlačeny, pokud dojde k následující:

- Systém obdrží oznámení o nedostatku paměti z operačního systému.

- Kód aplikace indukuje <xref:System.GC.Collect%2A?displayProperty=nameWithType> kolekci voláním `generation` metody a zadáním 2 pro parametr.

## <a name="scenarios"></a>Scénáře

V následující tabulce jsou uvedeny <xref:System.Runtime.GCLatencyMode> scénáře aplikace pro použití hodnot:

|Latence režim|Scénáře aplikací|
|------------------|---------------------------|
|<xref:System.Runtime.GCLatencyMode.Batch>|Pro aplikace, které nemají žádné uživatelské rozhraní (UI) nebo operace na straně serveru.<br /><br />Pokud je uvolňování paměti na pozadí zakázáno, jedná se o výchozí režim pro uvolňování paměti pracovní stanice a serveru. <xref:System.Runtime.GCLatencyMode.Batch>režim také přepíše nastavení [gcConcurrent,](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) to znamená, že zabraňuje pozadí nebo souběžných kolekcí.|
|<xref:System.Runtime.GCLatencyMode.Interactive>|Pro většinu aplikací, které mají ui.<br /><br />Toto je výchozí režim pro uvolňování paměti pracovní stanice a serveru. Pokud je však aplikace hostována, mají přednost nastavení uvolňování paměti hostitelského procesu.|
|<xref:System.Runtime.GCLatencyMode.LowLatency>|Pro aplikace, které mají krátkodobé, časově citlivé operace, během kterého přerušení z uvolňování může být rušivé. Například aplikace, které vykreslují animace nebo funkce pro sběr dat.|
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|Pro aplikace, které mají časově citlivé operace pro uzavřené, ale potenciálně delší dobu trvání, během kterého přerušení z uvolňování může být rušivé. Například aplikace, které potřebují rychlou odezvu, protože se během obchodních hodin mění údaje o trhu.<br /><br />Výsledkem tohoto režimu je větší velikost spravované haldy než jiné režimy. Vzhledem k tomu, že není komprimovat spravované haldy, vyšší fragmentace je možné. Ujistěte se, že je k dispozici dostatek paměti.|

## <a name="guidelines-for-using-low-latency"></a>Pokyny pro použití s nízkou latencí

Při použití [režimu GCLatencyMode.LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) zvažte následující pokyny:

- Udržujte časové období v nízké latenci co nejkratší.

- Vyhněte se přidělování vysoké množství paměti během období s nízkou latencí. Oznámení nedostatku paměti může dojít, protože uvolňování paměti uvolňuje méně objektů.

- Zatímco v režimu s nízkou latencí, minimalizovat počet nových přidělení, zejména přidělení na haldy velkého objektu a připnuté objekty.

- Mějte na paměti podprocesy, které by mohly být přidělování. Vzhledem <xref:System.Runtime.GCSettings.LatencyMode%2A> k tomu, že <xref:System.OutOfMemoryException> nastavení vlastnosti je celý proces, výjimky mohou být generovány v libovolném vlákně, které je přidělování.

- Zalomit kód s nízkou latencí v oblastech omezené spuštění. Další informace naleznete [v tématu Oblasti omezeného provádění](../../../docs/framework/performance/constrained-execution-regions.md).

- Můžete vynutit generování 2 kolekce během období <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> s nízkou latencí voláním metody.

## <a name="see-also"></a>Viz také

- <xref:System.GC?displayProperty=nameWithType>
- [Vyvolané kolekce](../../../docs/standard/garbage-collection/induced.md)
- [Kolekce paměti](../../../docs/standard/garbage-collection/index.md)
