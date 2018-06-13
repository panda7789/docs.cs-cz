---
title: Vyvolané kolekce
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 436953782049800e89298932278af4e450fc10de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575860"
---
# <a name="induced-collections"></a>Vyvolané kolekce
Ve většině případů může systém uvolňování paměti určit nejvhodnější čas k provedení uvolnění paměti, které byste pak měli nechat běžet nezávisle. Při vynuceném kolekce může zlepšit výkon vaší aplikace, se velmi zřídka. V těchto případech můžete vyvolat uvolňování paměti pomocí <xref:System.GC.Collect%2A?displayProperty=nameWithType> metoda vynutit uvolnění paměti.  
  
 Použití <xref:System.GC.Collect%2A?displayProperty=nameWithType> metoda, když dojde k výraznému snížení množství paměti použité v určitém bodě v kódu aplikace. Například pokud vaše aplikace používá komplexní dialogové okno, který má několik ovládacích prvků, volání <xref:System.GC.Collect%2A> při uzavření dialogové okno může zvýšit výkon, okamžitě opětovného získání množství paměti používané dialogové okno. Ujistěte se, že vaše aplikace není vyvolat uvolňování příliš často, vzhledem k tomu, který může snížit výkon, pokud má systém uvolňování se pokouší uvolnit objekty v jiných optimální časech. Můžete zadat <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> hodnotu výčtu <xref:System.GC.Collect%2A> metoda shromažďovat jenom v případě, že kolekce by být produktivní, jak je popsáno v následující části.  
  
## <a name="gc-collection-mode"></a>Režim kolekce uvolňování paměti  
 Můžete použít jednu z <xref:System.GC.Collect%2A?displayProperty=nameWithType> přetížení metody, které zahrnuje <xref:System.GCCollectionMode> hodnotu, která určuje chování pro kolekci vynucené následujícím způsobem.  
  
|`GCCollectionMode` Hodnota|Popis|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|Používá výchozí nastavení kolekce uvolňování paměti pro spuštěné verze rozhraní .NET.|  
|<xref:System.GCCollectionMode.Forced>|Vynutí uvolňování proběhnout okamžitě. Jde o ekvivalent volání <xref:System.GC.Collect?displayProperty=nameWithType> přetížení. Výsledkem úplné blokující kolekce všech generací.<br /><br /> Velkého objektu haldy můžete také zkomprimovat nastavením <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> vlastnost <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> před vynucením okamžité úplné blokování uvolňování paměti.|  
|<xref:System.GCCollectionMode.Optimized>|Umožňuje garbage collector v k určení, zda je aktuální čas optimální uvolnění objektů.<br /><br /> Uvolňování paměti mohou určit, že kolekce nebude dostatečně produktivní, chcete-li být zarovnán do bloku, v takovém případě bude vrátit bez opětovného získání objekty.|  
  
## <a name="background-or-blocking-collections"></a>Pozadí nebo blokujících kolekcí  
 Můžete volat <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType> přetížení metody k určení, zda je zablokovaná vyvolané kolekce, nebo ne. Typ kolekce provést závisí na kombinaci metody `mode` a `blocking` parametry. `mode` je členem skupiny <xref:System.GCCollectionMode> výčtu a `blocking` je <xref:System.Boolean> hodnotu. Následující tabulka shrnuje interakci `mode` a `blocking` argumenty.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> Nebo <xref:System.GCCollectionMode.Default>|Blokující kolekce se provádí co nejdříve. Pokud probíhá na pozadí shromažďování a generování je 0 nebo 1, <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> metoda ihned aktivuje blokující kolekce a vrátí po dokončení kolekce. Pokud probíhá na pozadí kolekce a `generation` parametr je 2, metoda počká, dokud kolekci pozadí po dokončení, aktivuje blokující kolekce 2. generace a potom se vrátí.|Kolekce se provádí co nejdříve. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> Metoda požadavky kolekce pozadí, ale to není zaručena; v závislosti na v případech, může stále provádí blokující kolekce. Pokud je kolekce pozadí již probíhá, vrátí metoda okamžitě.|  
|<xref:System.GCCollectionMode.Optimized>|Blokující kolekce může provést, v závislosti na stavu systému uvolňování paměti a `generation` parametr. Uvolňování paměti se pokusí zajistit optimální výkon.|Kolekce může provést, v závislosti na stavu systému uvolňování paměti. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> Metoda požadavky kolekce pozadí, ale to není zaručena; v závislosti na v případech, může stále provádí blokující kolekce. Uvolňování paměti se pokusí zajistit optimální výkon. Pokud je kolekce pozadí již probíhá, vrátí metoda okamžitě.|  
  
## <a name="see-also"></a>Viz také  
 [Latentní režimy](../../../docs/standard/garbage-collection/latency.md)  
 [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
