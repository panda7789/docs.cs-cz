---
title: Vyvolané kolekce
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
ms.openlocfilehash: 604b49ef577a46204b523ebf5a8575a30b81635e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120923"
---
# <a name="induced-collections"></a>Vyvolané kolekce
Ve většině případů může systém uvolňování paměti určit nejvhodnější čas k provedení uvolnění paměti, které byste pak měli nechat běžet nezávisle. Existují vzácná situace, kdy může vynucená kolekce zlepšit výkon vaší aplikace. V těchto případech můžete vyvolat uvolňování paměti pomocí metody <xref:System.GC.Collect%2A?displayProperty=nameWithType> k vynucení uvolnění paměti.  
  
 Metodu <xref:System.GC.Collect%2A?displayProperty=nameWithType> použijte v případě, že dojde k výraznému snížení množství paměti, které se používá v určitém bodě kódu vaší aplikace. Například pokud vaše aplikace používá komplexní dialogové okno, které má několik ovládacích prvků, volání <xref:System.GC.Collect%2A> při zavření dialogového okna může zvýšit výkon tím, že okamžitě uvolní paměť využívanou dialogovým oknem. Ujistěte se, že aplikace neprovádí uvolňování paměti příliš často, protože může snížit výkon, pokud se systém uvolňování paměti snaží uvolnit objekty v neoptimálních časech. Můžete předat <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> hodnotu výčtu do metody <xref:System.GC.Collect%2A>, která se má shromažďovat pouze v případě, že by kolekce byla produktivní, jak je popsáno v další části.  
  
## <a name="gc-collection-mode"></a>Režim shromažďování GC  
 Můžete použít jedno z přetížení metod <xref:System.GC.Collect%2A?displayProperty=nameWithType>, které obsahují <xref:System.GCCollectionMode> hodnotu k určení chování pro vynucenou kolekci následujícím způsobem.  
  
|hodnota `GCCollectionMode`|Popis|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|Používá výchozí nastavení uvolňování paměti pro běžící verzi rozhraní .NET.|  
|<xref:System.GCCollectionMode.Forced>|Vynutí, aby se uvolňování paměti staly okamžitě. To je ekvivalentní volání přetížení <xref:System.GC.Collect?displayProperty=nameWithType>. Výsledkem je úplná blokující kolekce všech generací.<br /><br /> Můžete také zkomprimovat haldu velkých objektů nastavením vlastnosti <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> na <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> před vynucením okamžitého úplného blokování uvolňování paměti.|  
|<xref:System.GCCollectionMode.Optimized>|Umožňuje systému uvolňování paměti určit, zda je aktuální čas optimální pro uvolnění objektů.<br /><br /> Systém uvolňování paměti může určit, že kolekce nebude dostatečně produktivní, aby mohla být odůvodněná. v takovém případě se vrátí bez opětovného získání objektů.|  
  
## <a name="background-or-blocking-collections"></a>Pozadí nebo blokující kolekce  
 Můžete volat přetížení metody <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType>, abyste určili, zda volaný kolekce blokuje nebo není. Typ provedené kolekce závisí na kombinaci parametrů `mode` a `blocking` metody. `mode` je členem výčtu <xref:System.GCCollectionMode> a `blocking` je <xref:System.Boolean> hodnota. Následující tabulka shrnuje interakci `mode` a `blocking`ch argumentů.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> nebo <xref:System.GCCollectionMode.Default>|Blokující kolekce se provádí co nejrychleji. Pokud probíhá shromažďování na pozadí a generace je 0 nebo 1, metoda <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> okamžitě spustí blokující kolekci a vrátí po dokončení kolekce. Pokud probíhá shromažďování na pozadí a parametr `generation` je 2, bude metoda čekat na dokončení kolekce na pozadí, spustí blokování blokující 2 kolekce a poté se vrátí.|Kolekce se provádí co nejrychleji. Metoda <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> požaduje kolekci na pozadí, ale není zaručena; v závislosti na okolnostech může být stále prováděna blokující kolekce. Pokud kolekce na pozadí již probíhá, metoda se vrátí okamžitě.|  
|<xref:System.GCCollectionMode.Optimized>|Blokování kolekce může být provedeno v závislosti na stavu systému uvolňování paměti a parametru `generation`. Systém uvolňování paměti se pokusí poskytnout optimální výkon.|Kolekce může být provedena v závislosti na stavu systému uvolňování paměti. Metoda <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> požaduje kolekci na pozadí, ale není zaručena; v závislosti na okolnostech může být stále prováděna blokující kolekce. Systém uvolňování paměti se pokusí poskytnout optimální výkon. Pokud kolekce na pozadí již probíhá, metoda se vrátí okamžitě.|  
  
## <a name="see-also"></a>Viz také:

- [Latentní režimy](../../../docs/standard/garbage-collection/latency.md)
- [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
