---
title: "Kolekce se zabezpečenými vlákny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, overview
ms.assetid: 2e7ca21f-786c-4367-96be-0cf3f3dcc6bd
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ae53d5afbca15f8adafed428d4c2141312c972ed
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="thread-safe-collections"></a>Kolekce se zabezpečenými vlákny
[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] Zavádí <xref:System.Collections.Concurrent?displayProperty=nameWithType> názvů, který zahrnuje několik tříd kolekcí, které jsou bezpečné pro přístup z více vláken a škálovatelné. Více vláken může bezpečně a efektivně přidat nebo odebrat položky z těchto kolekcí, bez nutnosti další synchronizace v uživatelském kódu. Když píšete nový kód, pomocí třídy souběžných kolekce vždy, když kolekce se zápis do více vláken současně. Pokud jsou pouze čtení ze sdílené kolekce, pak můžete použít třídy v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů. Doporučujeme, abyste provedli třídy kolekcí verze 1.0, pokud není vyžadováno cílit na rozhraní .NET Framework 1.1 nebo starší modul runtime.  
  
## <a name="thread-synchronization-in-the-net-framework-10-and-20-collections"></a>Synchronizace vláken v rozhraní .NET Framework 1.0 a 2.0 kolekce  
 Kolekce zavedené v rozhraní .NET Framework 1.0 se nacházejí v <xref:System.Collections?displayProperty=nameWithType> oboru názvů. Tyto kolekce, které zahrnují běžně používané <xref:System.Collections.ArrayList> a <xref:System.Collections.Hashtable>, poskytovat některé vláken prostřednictvím `Synchronized` vlastnosti, která vrátí obálku kolem kolekce bezpečné pro přístup z více vláken. Obálku funguje tak, že na každé operace přidat nebo odebrat zamykání celou kolekci. Proto musí každý podproces, který se pokouší získat přístup ke kolekci čekat následně provést jeden zámek. Toto není škálovatelné a může způsobit významné snížení výkonu u rozsáhlých kolekcí. Návrh navíc není úplně chráněn před časování. Další informace najdete v tématu [synchronizace v obecné kolekce](http://go.microsoft.com/fwlink/?LinkID=161130) na webu MSDN.  
  
 Třídy kolekcí zavedené v rozhraní .NET Framework 2.0, které se nacházejí v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů. Mezi ně patří <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>a tak dále. Tyto třídy poskytují lepší typu zabezpečení a výkonu ve srovnání s třídy rozhraní .NET Framework 1.0. Kolekce tříd rozhraní .NET Framework 2.0 však neposkytuje žádnou synchronizaci vláken; Při přidávání nebo odebírání ve více vláknech souběžně položky, musíte zadat uživatelský kód veškeré synchronizaci.  
  
 Doporučujeme třídy souběžných kolekcí v [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] protože poskytují nejenom bezpečnost typů kolekce tříd rozhraní .NET Framework 2.0, ale také efektivnější a podrobnější zabezpečení vlákna, než [!INCLUDE[net_v10_short](../../../../includes/net-v10-short-md.md)] kolekce poskytují.  
  
## <a name="fine-grained-locking-and-lock-free-mechanisms"></a>Jemně odstupňovaných zamykání a uvolnění zámku mechanismy  
 Některé typy souběžných kolekcí používají mechanismy zjednodušené synchronizace, jako <xref:System.Threading.SpinLock>, <xref:System.Threading.SpinWait>, <xref:System.Threading.SemaphoreSlim>, a <xref:System.Threading.CountdownEvent>, které jsou v nové [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. Tyto typy synchronizace obvykle používají *zaneprázdnění* po krátkou dobu před jejich vlákno true stavu čekání. Když se měl velmi krátké doby čekání, roztočený je mnohem méně výpočetně náročné než čekání, které zahrnuje nákladný přechod jádra. Pro třídy kolekce, které používají zaneprázdnění této efektivity znamená, že můžete přidávat a odebírat položky velmi vysokou rychlostí více vláken. Další informace o roztočený oproti blokování najdete v tématu [SpinLock](../../../../docs/standard/threading/spinlock.md) a [objektu SpinWait](../../../../docs/standard/threading/spinwait.md).  
  
 <xref:System.Collections.Concurrent.ConcurrentQueue%601> a <xref:System.Collections.Concurrent.ConcurrentStack%601> třídy nepoužívejte zámky vůbec. Místo toho spoléhají na <xref:System.Threading.Interlocked> operace pro dosažení vláken.  
  
> [!NOTE]
>  Protože třídy souběžných kolekcí podporují <xref:System.Collections.ICollection>, poskytují implementace pro <xref:System.Collections.ICollection.IsSynchronized%2A> a <xref:System.Collections.ICollection.SyncRoot%2A> vlastnosti, i když tyto vlastnosti nejsou relevantní. `IsSynchronized`vždy vrátí hodnotu `false` a `SyncRoot` je vždy `null` (`Nothing` v jazyce Visual Basic).  
  
 Následující tabulka uvádí typy kolekcí v <xref:System.Collections.Concurrent?displayProperty=nameWithType> oboru názvů.  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601>|Poskytuje funkcí ohraničování a blokování pro žádný typ, který implementuje <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>. Další informace najdete v tématu [BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602>|Implementace bezpečné pro přístup z více vláken slovník páry klíč hodnota.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601>|Implementace bezpečné pro přístup z více vláken fronty FIFO (first in, první ven).|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601>|Implementace bezpečné pro přístup z více vláken zásobníku LIFO (last-in první ven).|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601>|Implementace bezpečné pro přístup z více vláken neuspořádaný kolekci elementů.|  
|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>|Rozhraní, které musí typ implementovat, který se má použít v `BlockingCollection`.|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)|Popisuje funkce poskytované službou <xref:System.Collections.Concurrent.BlockingCollection%601> typu.|  
|[Postupy: Přidávání a odebírání položek v ConcurrentDictionary](../../../../docs/standard/collections/thread-safe/how-to-add-and-remove-items.md)|Popisuje, jak přidávat a odebírat elementů od<xref:System.Collections.Concurrent.ConcurrentDictionary%602>|  
|[Postupy: Přidávání a odebírání jednotlivých položek v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)|Popisuje, jak přidat a načítat položky z blokující kolekce bez použití enumerátor jen pro čtení.|  
|[Postupy: Přidání funkcí ohraničování a blokování do kolekce](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md)|Popisuje, jak chcete použít jako základní mechanismus úložiště pro všechny třídy kolekce <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> kolekce.|  
|[Postupy: Použití příkazu ForEach k odebrání položek v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)|Popisuje způsob použití `foreach`, (`For Each` v jazyce Visual Basic) Chcete-li odebrat všechny položky v kolekci blokování.|  
|[Postupy: Použití polí blokujících kolekcí v datovém kanálu](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md)|Popisuje, jak používat více blokující kolekce ve stejnou dobu implementace kanálu.|  
|[Postupy: Vytvoření fondu objektů pomocí ConcurrentBag](../../../../docs/standard/collections/thread-safe/how-to-create-an-object-pool.md)|Zobrazuje způsob používání souběžného kontejneru za účelem zlepšení výkonu v situacích, kdy je možné namísto neustálého vytváření nových objektů opětovně používat stávající objekty.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>
