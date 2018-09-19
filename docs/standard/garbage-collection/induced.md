---
title: Vyvolané kolekce
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69590b0efc924132d149621c135ef0816cac7d1e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003052"
---
# <a name="induced-collections"></a>Vyvolané kolekce
Ve většině případů může systém uvolňování paměti určit nejvhodnější čas k provedení uvolnění paměti, které byste pak měli nechat běžet nezávisle. Existují výjimečné situace, kdy může vynucená kolekce zlepšit výkon vaší aplikace. V těchto případech můžete zahájit uvolnění pomocí <xref:System.GC.Collect%2A?displayProperty=nameWithType> metody pro vynucení uvolnění paměti.  
  
 Použití <xref:System.GC.Collect%2A?displayProperty=nameWithType> metodu, když dojde k výraznému snížení množství paměti používané v konkrétním bodě v kódu vaší aplikace. Například pokud vaše aplikace používá komplexní dialogové okno, které obsahuje několik ovládacích prvků, volání <xref:System.GC.Collect%2A> při ukončení dialogu může zlepšit výkon, protože okamžitě uvolní paměť používanou v dialogovém okně. Ujistěte se, že aplikace nevyvolá uvolnění paměti příliš často, protože pokud systému uvolňování paměti pokouší uvolnit objekty v neoptimálních časech, které může snížit výkon. Můžete zadat <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> hodnotu výčtu pro <xref:System.GC.Collect%2A> metoda shromažďovat pouze v případě, že kolekce by kolekce byla produktivní, jak je popsáno v další části.  
  
## <a name="gc-collection-mode"></a>Režim kolekce GC  
 Můžete použít jednu z <xref:System.GC.Collect%2A?displayProperty=nameWithType> přetížení metod, které zahrnuje <xref:System.GCCollectionMode> hodnota, která má specifikaci chování vynucené kolekce následujícím způsobem.  
  
|`GCCollectionMode` Hodnota|Popis|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|Použije výchozí nastavení kolekce uvolnění paměti pro spuštěnou verzi rozhraní .NET.|  
|<xref:System.GCCollectionMode.Forced>|Kolekce paměti vynutí okamžité. To je ekvivalentní volání <xref:System.GC.Collect?displayProperty=nameWithType> přetížení. Výsledkem je blokování celé kolekce všech generací.<br /><br /> Haldy velkých objektů můžete také zkomprimovat nastavením <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> vlastnost <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> před vynuceným okamžité úplné blokující uvolňování paměti kolekci.|  
|<xref:System.GCCollectionMode.Optimized>|Umožňuje uvolňování paměti určit, zda je aktuální čas optimální pro uvolnění objektů.<br /><br /> Uvolňování paměti může určit, že kolekce by nebyla dostatečně produktivní oprávněné, v takovém případě ji vrátí bez uvolní objektů.|  
  
## <a name="background-or-blocking-collections"></a>Pozadí nebo blokující kolekce  
 Můžete volat <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType> přetížení metody k určení, zda je blokována indukovaná kolekce blokování nebo ne. Provedený typ kolekce závisí na kombinaci metody `mode` a `blocking` parametry. `mode` je členem skupiny <xref:System.GCCollectionMode> výčtu, a `blocking` je <xref:System.Boolean> hodnotu. Následující tabulka shrnuje působení `mode` a `blocking` argumenty.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> Nebo <xref:System.GCCollectionMode.Default>|Blokující kolekce se provádí co nejdříve. Pokud probíhá shromažďování pozadí a generování je 0 nebo 1, <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> metoda okamžitě spustí z blokující kolekce a vrátí po dokončení kolekce. Pokud probíhá shromažďování pozadí a `generation` parametr bude 2, metoda čeká na pozadí je dokončená, spustí blokující generaci 2 kolekce a vrátí.|Kolekce se provádí co nejdříve. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> Metoda požaduje kolekci v pozadí, ale to není zaručeno, v závislosti na okolnostech mohou stále prováděny blokující kolekce. Pokud kolekce pozadí již probíhá, metoda vrátí hodnotu okamžitě.|  
|<xref:System.GCCollectionMode.Optimized>|Blokující kolekce mohou být provedeny v závislosti na stavu systému uvolňování paměti a `generation` parametru. Uvolňování paměti se snaží poskytovat optimální výkon.|Kolekce mohou být provedeny v závislosti na stavu systému uvolňování paměti. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> Metoda požaduje kolekci v pozadí, ale to není zaručeno, v závislosti na okolnostech mohou stále prováděny blokující kolekce. Uvolňování paměti se snaží poskytovat optimální výkon. Pokud kolekce pozadí již probíhá, metoda vrátí hodnotu okamžitě.|  
  
## <a name="see-also"></a>Viz také:

- [Latentní režimy](../../../docs/standard/garbage-collection/latency.md)  
- [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
