---
title: Vyvolané kolekce
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
ms.openlocfilehash: 36dff45587c6c28ba17fd7389dc3863893ff8f61
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286038"
---
# <a name="induced-collections"></a>Vyvolané kolekce
Ve většině případů může systém uvolňování paměti určit nejvhodnější čas k provedení uvolnění paměti, které byste pak měli nechat běžet nezávisle. Existují vzácná situace, kdy může vynucená kolekce zlepšit výkon vaší aplikace. V těchto případech můžete vyvolat uvolňování paměti pomocí <xref:System.GC.Collect%2A?displayProperty=nameWithType> metody k vynucení uvolňování paměti.  
  
 Použijte metodu, pokud dojde k <xref:System.GC.Collect%2A?displayProperty=nameWithType> výraznému snížení množství paměti, které se používá v určitém bodě kódu vaší aplikace. Například pokud vaše aplikace používá komplexní dialogové okno, které má několik ovládacích prvků, volání <xref:System.GC.Collect%2A> při zavření dialogového okna může zvýšit výkon tím, že okamžitě uvolní paměť, kterou používá dialogové okno. Ujistěte se, že aplikace neprovádí uvolňování paměti příliš často, protože může snížit výkon, pokud se systém uvolňování paměti snaží uvolnit objekty v neoptimálních časech. Můžete předat <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> hodnotu výčtu do <xref:System.GC.Collect%2A> metody, která bude shromažďována pouze v případě, že by došlo k produktivnímu shromažďování, jak je popsáno v následující části.  
  
## <a name="gc-collection-mode"></a>Režim shromažďování GC  
 Můžete použít jedno z <xref:System.GC.Collect%2A?displayProperty=nameWithType> přetížení metod, které obsahuje <xref:System.GCCollectionMode> hodnotu k určení chování pro vynucenou kolekci následujícím způsobem.  
  
|`GCCollectionMode`osa|Popis|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|Používá výchozí nastavení uvolňování paměti pro běžící verzi rozhraní .NET.|  
|<xref:System.GCCollectionMode.Forced>|Vynutí, aby se uvolňování paměti staly okamžitě. To je ekvivalentní volání <xref:System.GC.Collect?displayProperty=nameWithType> přetížení. Výsledkem je úplná blokující kolekce všech generací.<br /><br /> Můžete také zkomprimovat haldu velkých objektů nastavením <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> vlastnosti na hodnotu <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> před vynucením okamžitého úplného blokování uvolňování paměti.|  
|<xref:System.GCCollectionMode.Optimized>|Umožňuje systému uvolňování paměti určit, zda je aktuální čas optimální pro uvolnění objektů.<br /><br /> Systém uvolňování paměti může určit, že kolekce nebude dostatečně produktivní, aby mohla být odůvodněná. v takovém případě se vrátí bez opětovného získání objektů.|  
  
## <a name="background-or-blocking-collections"></a>Pozadí nebo blokující kolekce  
 Můžete volat <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType> přetížení metody, chcete-li určit, zda volaný kolekce blokuje nebo není. Typ provedené kolekce závisí na kombinaci `mode` parametrů a metody `blocking` . `mode`je členem <xref:System.GCCollectionMode> výčtu a `blocking` je <xref:System.Boolean> hodnota. Následující tabulka shrnuje interakce `mode` `blocking` argumentů a.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> nebo <xref:System.GCCollectionMode.Default>|Blokující kolekce se provádí co nejrychleji. Pokud probíhá shromažďování na pozadí a generace je 0 nebo 1, <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> Metoda okamžitě spustí blokující kolekci a vrátí po dokončení kolekce. Pokud probíhá shromažďování na pozadí a `generation` parametr je 2, metoda počká, dokud není dokončeno shromažďování na pozadí, spustí blokující kolekci 2 a potom vrátí.|Kolekce se provádí co nejrychleji. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29>Metoda požaduje kolekci na pozadí, ale není zaručena. v závislosti na okolnostech může být stále prováděna blokující kolekce. Pokud kolekce na pozadí již probíhá, metoda se vrátí okamžitě.|  
|<xref:System.GCCollectionMode.Optimized>|Blokování kolekce může být provedeno v závislosti na stavu systému uvolňování paměti a `generation` parametru. Systém uvolňování paměti se pokusí poskytnout optimální výkon.|Kolekce může být provedena v závislosti na stavu systému uvolňování paměti. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29>Metoda požaduje kolekci na pozadí, ale není zaručena. v závislosti na okolnostech může být stále prováděna blokující kolekce. Systém uvolňování paměti se pokusí poskytnout optimální výkon. Pokud kolekce na pozadí již probíhá, metoda se vrátí okamžitě.|  
  
## <a name="see-also"></a>Viz také

- [Režimy latence](latency.md)
- [Uvolňování paměti](index.md)
