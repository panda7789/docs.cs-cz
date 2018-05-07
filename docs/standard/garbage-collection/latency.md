---
title: Latentní režimy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 913a5d6ab28d375dbfdd99dec6fd153bc94efee5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="latency-modes"></a>Latentní režimy
Uvolnění objektů, musí uvolňování zastavení všech spuštěných vláken v aplikaci. V některých situacích, například pokud aplikace načte data nebo se zobrazí obsah můžete na kritické čas úplné uvolnění paměti a mít dopad na výkon. Míra interakce systému uvolňování můžete upravit podle nastavení <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> vlastnost na jednu z <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> hodnoty.  
  
 Latence odkazuje na čas, který má systém uvolňování intrudes ve vaší aplikaci. Uvolňování paměti během období s nízkou latencí, je více konzervativní a šetrnější v opětovného získání objekty. <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> Výčtu poskytuje dvě nastavení s nízkou latencí:  
  
-   <xref:System.Runtime.GCLatencyMode.LowLatency> Potlačí 2. generace kolekce a provádí pouze kolekce, generace 0 a 1. Lze pouze na krátkou dobu. Delší období Pokud systém je přetížena paměť, aktivují garbage collector v kolekci, která můžete stručně pozastavit aplikace a přerušit kritický pro čas operace. Toto nastavení je dostupné pouze pro uvolňování paměti pracovních stanic.  
  
-   <xref:System.Runtime.GCLatencyMode.SustainedLowLatency> Potlačí popředí 2. generace kolekce a provede jenom generace 0, 1, 2. generace kolekce pozadí. Lze použít pro delší časové období a je k dispozici pro uvolňování paměti serveru a pracovní stanice. Toto nastavení nelze použít, pokud [souběžné uvolňování](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) je zakázána.  
  
 Během období s nízkou latencí jsou potlačovány 2. generace kolekce, pokud dojde k následujícímu:  
  
-   Systém obdrží upozornění na nedostatek paměti z operačního systému.  
  
-   Kód aplikace indukuje kolekce voláním <xref:System.GC.Collect%2A?displayProperty=nameWithType> metoda a zadání 2 pro `generation` parametr.  
  
 Následující tabulka uvádí scénáře aplikací pro použití <xref:System.Runtime.GCLatencyMode> hodnoty.  
  
|Latence režimu|Scénáře aplikací|  
|------------------|---------------------------|  
|<xref:System.Runtime.GCLatencyMode.Batch>|Pro aplikace, které mají žádné uživatelské rozhraní nebo operací na straně serveru.<br /><br /> Toto je výchozí režim při [souběžné uvolňování](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) je zakázána.|  
|<xref:System.Runtime.GCLatencyMode.Interactive>|Pro většinu aplikací, které mají uživatelského rozhraní.<br /><br /> Toto je výchozí režim při [souběžné uvolňování](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) je povoleno.|  
|<xref:System.Runtime.GCLatencyMode.LowLatency>|Pro aplikace, které mají krátkodobé může být rušivý operace citlivé na čas, během které přerušení z uvolňování paměti. Například aplikace, které provádějí animace funkce pořízení vykreslování nebo data.|  
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|Pro aplikace, které mají operace náročné na čas pro dobu trvání obsažené ale potenciálně delší dobu, během kterého může být rušivý přerušení z uvolňování paměti. Například aplikace, které potřebují rychlý odezvy jako změny dat trhu obchodním dobu.<br /><br /> Tento režim za následek větší velikost spravovaná halda než jiné režimy. Protože je komprimovat není spravovaná halda, je možné vyšší fragmentace. Ujistěte se, že je k dispozici dostatek paměti.|  
  
## <a name="guidelines-for-using-low-latency"></a>Pokyny k používání s nízkou latencí  
 Při použití <xref:System.Runtime.GCLatencyMode.LowLatency> režimu, vezměte v úvahu následující skutečnosti:  
  
-   Doba, mějte s nízkou latencí co nejkratší.  
  
-   Vyhněte se přidělování vysoké objemy paměti během období s nízkou latencí. Nedostatek paměti oznámení může dojít, protože uvolňování paměti získá méně objektů.  
  
-   V režimu s nízkou latencí, Minimalizujte počet přidělení, které provedete v konkrétní přidělení do velkého objektu haldy a definovaného objekty.  
  
-   Uvědomte si, vláken, která by mohla být přidělení. Protože <xref:System.Runtime.GCSettings.LatencyMode%2A> je nastavení vlastnosti procesy, může způsobit <xref:System.OutOfMemoryException> na jakékoli vlákno, které může být přidělení.  
  
-   Zalomení kód s nízkou latencí v omezené oblasti provádění (Další informace najdete v tématu [omezené oblasti provádění](../../../docs/framework/performance/constrained-execution-regions.md)).  
  
-   2. generace kolekce můžete vynutit během období s nízkou latencí při volání <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> metoda.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.GC?displayProperty=nameWithType>  
 [Vyvolané kolekce](../../../docs/standard/garbage-collection/induced.md)  
 [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
