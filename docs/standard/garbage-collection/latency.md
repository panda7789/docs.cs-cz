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
ms.openlocfilehash: 7a81a0015ae046682e1afa40c1c8d272357839ba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622786"
---
# <a name="latency-modes"></a>Latentní režimy
Uvolnit objekty, uvolňování, musíte zastavit všechna vlákna provádění v aplikaci. V některých situacích, například když aplikace načítá data nebo zobrazí obsah úplné uvolnění paměti dochází při kritické době a bránit ve výkonu. Můžete upravit parametry systému uvolňování paměti tak, že nastavíte <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> vlastnost na jednu z <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> hodnoty.  
  
 Latence odkazuje na čas, který intrudes systému uvolňování paměti v aplikaci. Během období s nízkou latencí uvolňování paměti je konzervativnější a teď míň obtěžující v uvolní objektů. <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> Výčet poskytuje dvě nastavení s nízkou latencí:  
  
- <xref:System.Runtime.GCLatencyMode.LowLatency> Potlačí kolekce generace 2 a provádí pouze kolekce generace 0 a 1. Je možné jenom za krátkou dobu. Časových obdobích Pokud systém je přetížena paměť, aktivuje systému uvolňování paměti kolekce, která může stručně pozastavení aplikace nebo narušit náročné operace. Toto nastavení je dostupné pouze pro uvolnění paměti pracovní stanice.  
  
- <xref:System.Runtime.GCLatencyMode.SustainedLowLatency> Potlačí popředí generace 2 kolekce a provádí pouze generace 0, 1 a 2. generace kolekce na pozadí. Lze použít pro delší dobu a je k dispozici pro uvolnění paměti pracovní stanice a serveru. Toto nastavení nelze použít, pokud [souběžné uvolňování paměti](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) je zakázaná.  
  
 Během období s nízkou latencí kolekce generace 2 jsou potlačeny, pokud dojde k následujícímu:  
  
- Systém obdrží upozornění na nedostatek paměti z operačního systému.  
  
- Kód aplikace indukuje kolekce voláním <xref:System.GC.Collect%2A?displayProperty=nameWithType> metoda a 2 pro zadání `generation` parametru.  
  
 Následující tabulka uvádí scénáře aplikací pro použití <xref:System.Runtime.GCLatencyMode> hodnoty.  
  
|Latence režimu|Scénáře aplikací|  
|------------------|---------------------------|  
|<xref:System.Runtime.GCLatencyMode.Batch>|U aplikací, které mají bez uživatelského rozhraní nebo operací na straně serveru.<br /><br /> Toto je výchozí režim při [souběžné uvolňování paměti](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) je zakázaná.|  
|<xref:System.Runtime.GCLatencyMode.Interactive>|Pro většinu aplikací, které mají uživatelské rozhraní.<br /><br /> Toto je výchozí režim při [souběžné uvolňování paměti](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) je povolená.|  
|<xref:System.Runtime.GCLatencyMode.LowLatency>|Pro aplikace, které mají krátkodobé operace citlivé na čas, během které přerušení ze systému uvolňování paměti může působit rušivě. Například aplikace, které provádějí animace funkce pořízení vykreslování nebo data.|  
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|Pro aplikace, které mají časově závislé operace pro dobu trvání omezením, ale potenciálně delší dobu, během které přerušení ze systému uvolňování paměti může působit rušivě. Například aplikace, které potřebujete rychlou dobu odezvy u jako změny dat na trhu obchodních hodin.<br /><br /> Tento režim za následek větší velikost než jiné režimy spravované haldě. Protože to není compact spravované haldě, je možné vyšší fragmentace. Ujistěte se, že je k dispozici dostatek paměti.|  
  
## <a name="guidelines-for-using-low-latency"></a>Pokyny k použití s nízkou latencí  
 Při použití <xref:System.Runtime.GCLatencyMode.LowLatency> režimu, vezměte v úvahu následující pokyny:  
  
- Zachovat časový interval, v co nejkratší s nízkou latencí.  
  
- Vyhněte se přidělování vysoké množství paměti během období s nízkou latencí. Oznámení nedostatku paměti může dojít, protože uvolňování paměti získá méně objektů.  
  
- V režimu s nízkou latencí, Minimalizujte počet přidělení, které provedete v konkrétní přidělení na připojených objektů a haldy pro velké objekty.  
  
- Mějte na paměti vláken, které by mohly být přidělování. Protože <xref:System.Runtime.GCSettings.LatencyMode%2A> vlastnost nastavena na hodnotu celého procesu, může generovat <xref:System.OutOfMemoryException> v libovolném vlákně, který může být přidělení.  
  
- Zabalit do oblasti omezeného provádění kódu s nízkou latencí (Další informace najdete v tématu [oblasti omezeného provádění](../../../docs/framework/performance/constrained-execution-regions.md)).  
  
- Kolekce generace 2 v období nízké latence můžete vynutit pomocí volání <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> metody.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.GC?displayProperty=nameWithType>
- [Vyvolané kolekce](../../../docs/standard/garbage-collection/induced.md)
- [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
