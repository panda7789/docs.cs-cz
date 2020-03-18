---
title: Vyvolané kolekce
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
ms.openlocfilehash: 604b49ef577a46204b523ebf5a8575a30b81635e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120923"
---
# <a name="induced-collections"></a>Vyvolané kolekce
Ve většině případů může systém uvolňování paměti určit nejvhodnější čas k provedení uvolnění paměti, které byste pak měli nechat běžet nezávisle. Existují vzácné situace, kdy vynucená kolekce může zlepšit výkon vaší aplikace. V těchto případech můžete vyvolat uvolňování <xref:System.GC.Collect%2A?displayProperty=nameWithType> paměti pomocí metody vynutit uvolnění paměti.  
  
 Metodu <xref:System.GC.Collect%2A?displayProperty=nameWithType> použijte, pokud dojde k významnému snížení množství paměti používané v určitém bodě v kódu aplikace. Pokud například aplikace používá složité dialogové okno s <xref:System.GC.Collect%2A> několika ovládacími prvky, volání při zavření dialogového okna může zvýšit výkon okamžitým obnovením paměti používané v dialogovém okně. Ujistěte se, že vaše aplikace není vyvolání uvolňování paměti příliš často, protože to může snížit výkon, pokud systém uvolňování paměti se pokouší získat objekty v neoptimálních časech. Můžete zadat <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> výčet hodnotu <xref:System.GC.Collect%2A> metody shromažďovat pouze v případě, že kolekce by být produktivní, jak je popsáno v další části.  
  
## <a name="gc-collection-mode"></a>Režim kolekce GC  
 Můžete použít jeden <xref:System.GC.Collect%2A?displayProperty=nameWithType> z přetížení metody, <xref:System.GCCollectionMode> která obsahuje hodnotu k určení chování pro vynucené kolekce takto.  
  
|`GCCollectionMode`Hodnotu|Popis|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|Používá výchozí nastavení uvolňování paměti pro spuštěnou verzi rozhraní .NET.|  
|<xref:System.GCCollectionMode.Forced>|Vynutí uvolnění paměti dojít okamžitě. To je ekvivalentní <xref:System.GC.Collect?displayProperty=nameWithType> volání přetížení. Výsledkem je úplné blokování kolekce všech generací.<br /><br /> Můžete také komprimovat haldy <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> velkých <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> objektů nastavením vlastnost před vynucením okamžité úplné blokování uvolňování paměti.|  
|<xref:System.GCCollectionMode.Optimized>|Umožňuje uvolňování paměti určit, zda aktuální čas je optimální pro uvolnění objektů.<br /><br /> Systém uvolňování paměti může určit, že kolekce by nebyla dostatečně produktivní, aby byla zarovnaná, v takovém případě se vrátí bez uvolnění objektů.|  
  
## <a name="background-or-blocking-collections"></a>Pozadí nebo blokování kolekcí  
 Můžete volat <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType> přetížení metody určit, zda indukované kolekce je blokování nebo ne. Typ kolekce závisí na kombinaci metody `mode` a `blocking` parametry. `mode`je členem výčtu <xref:System.GCCollectionMode> a `blocking` je <xref:System.Boolean> hodnota. Následující tabulka shrnuje interakci `mode` `blocking` a argumenty.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> nebo <xref:System.GCCollectionMode.Default>|Blokování kolekce se provádí co nejdříve. Pokud probíhá kolekce na pozadí a generování <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> je 0 nebo 1, metoda okamžitě aktivuje blokování kolekce a vrátí po dokončení kolekce. Pokud probíhá kolekce pozadí `generation` a parametr je 2, metoda čeká, dokud je dokončena kolekce pozadí, aktivuje blokování generace 2 kolekce a vrátí.|Kolekce se provádí co nejdříve. Metoda <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> požaduje kolekci na pozadí, ale to není zaručeno; v závislosti na okolnostech může být stále prováděna blokační kolekce. Pokud kolekce pozadí již probíhá, metoda vrátí okamžitě.|  
|<xref:System.GCCollectionMode.Optimized>|Blokování kolekce může být provedena, v závislosti na `generation` stavu systému uvolňování paměti a parametr. Systém uvolňování paměti se pokusí poskytnout optimální výkon.|V závislosti na stavu systému uvolňování paměti může být provedena kolekce. Metoda <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> požaduje kolekci na pozadí, ale to není zaručeno; v závislosti na okolnostech může být stále prováděna blokační kolekce. Systém uvolňování paměti se pokusí poskytnout optimální výkon. Pokud kolekce pozadí již probíhá, metoda vrátí okamžitě.|  
  
## <a name="see-also"></a>Viz také

- [Latentní režimy](../../../docs/standard/garbage-collection/latency.md)
- [Kolekce paměti](../../../docs/standard/garbage-collection/index.md)
