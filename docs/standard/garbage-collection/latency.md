---
title: Latentní režimy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: 8833c88c3221c0a375011eb62dd712340f7e89cd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120911"
---
# <a name="latency-modes"></a>Latentní režimy
Chcete-li uvolnit objekty, systém uvolňování paměti musí zastavit všechna spuštěná vlákna v aplikaci. V některých situacích, například když aplikace načítá data nebo zobrazuje obsah, může v kritickém čase dojít k úplnému uvolňování paměti a brání se tak výkonu. Můžete upravit rušivost systému uvolňování paměti nastavením vlastnosti <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> na jednu z hodnot <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>.  
  
 Latence odkazuje na čas, který systém uvolňování paměti intrudes ve vaší aplikaci. Během období s nízkou latencí je systém uvolňování paměti více konzervativní a méně rušivý při uvolnění objektů. Výčet <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> poskytuje dvě nastavení s nízkou latencí:  
  
- <xref:System.Runtime.GCLatencyMode.LowLatency> potlačí kolekce 2. generace a provede pouze kolekce generace 0 a 1. Dá se použít jenom pro krátkou dobu. V delší dobu, pokud je systém v paměti, uvolňování paměti spustí kolekci, která může krátce pozastavit aplikaci a rušit kritické operace. Toto nastavení je dostupné jenom pro uvolňování paměti pracovní stanice.  
  
- <xref:System.Runtime.GCLatencyMode.SustainedLowLatency> potlačí kolekce na popředí 2. generace a provede pouze kolekce generace 0, 1 a Background generace 2. Dá se použít po delší dobu a je k dispozici pro pracovní stanici i pro uvolňování paměti serveru. Toto nastavení se nedá použít, pokud je zakázané [souběžné uvolňování paměti](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) .  
  
 Během období s nízkou latencí jsou kolekce 2. generace potlačeny, pokud nedojde k následujícím akcím:  
  
- Systém obdrží oznámení o nedostatku paměti z operačního systému.  
  
- Kód aplikace vyvolá kolekci voláním metody <xref:System.GC.Collect%2A?displayProperty=nameWithType> a zadáním 2 pro parametr `generation`.  
  
 V následující tabulce je uveden seznam scénářů aplikací pro použití <xref:System.Runtime.GCLatencyMode>ch hodnot.  
  
|Režim latence|Scénáře aplikací|  
|------------------|---------------------------|  
|<xref:System.Runtime.GCLatencyMode.Batch>|Pro aplikace, které nemají žádné uživatelské rozhraní ani serverové operace.<br /><br /> Toto je výchozí režim, pokud je zakázané [souběžné uvolňování paměti](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) .|  
|<xref:System.Runtime.GCLatencyMode.Interactive>|Pro většinu aplikací, které mají uživatelské rozhraní.<br /><br /> Toto je výchozí režim, pokud je povoleno [souběžné uvolňování paměti](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) .|  
|<xref:System.Runtime.GCLatencyMode.LowLatency>|Pro aplikace, které mají krátkodobé, časově citlivé operace, během kterých by mohlo dojít k přerušení výpadků ze systému uvolňování paměti. Například aplikace, které vykreslují animace nebo funkce pro získání dat.|  
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|Pro aplikace, které mají časově náročné operace pro obsaženou, ale potenciálně delší dobu, kdy může dojít k přerušení výpadků ze systému uvolňování paměti. Například aplikace, které vyžadují dobu trvání rychlé odezvy v době, kdy se mění data trhu během doby obchodování.<br /><br /> Výsledkem tohoto režimu je větší spravovaná velikost haldy než jiné režimy. Vzhledem k tomu, že nástroj nekomprimuje spravovanou haldu, je možné zvýšit fragmentaci. Ujistěte se, že je k dispozici dostatek paměti.|  
  
## <a name="guidelines-for-using-low-latency"></a>Pokyny pro použití nízké latence  
 Při použití režimu <xref:System.Runtime.GCLatencyMode.LowLatency> Vezměte v úvahu následující pokyny:  
  
- Udržujte dobu v nízké latenci, která je co nejkratší.  
  
- Vyhněte se přidělování vysoké velikosti paměti během období s nízkou latencí. K oznamování nedostatku paměti může dojít, protože uvolňování paměti uvolňuje méně objektů.  
  
- V režimu s nízkou latencí Minimalizujte počet přidělených přidělení, zejména přidělení na Large Object haldu a připnuté objekty.  
  
- Upozorňujeme na vlákna, která by se dala přidělit. Vzhledem k tomu, že nastavení vlastnosti <xref:System.Runtime.GCSettings.LatencyMode%2A> je v rámci procesu, můžete vygenerovat <xref:System.OutOfMemoryException> na jakémkoli vlákně, které může být přiděleno.  
  
- Zabalte kód nízké latence v oblastech omezeného provádění (Další informace najdete v tématu [omezené oblasti provádění](../../../docs/framework/performance/constrained-execution-regions.md)).  
  
- Můžete vynutit kolekce 2. generace během období s nízkou latencí voláním metody <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.GC?displayProperty=nameWithType>
- [Vyvolané kolekce](../../../docs/standard/garbage-collection/induced.md)
- [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
