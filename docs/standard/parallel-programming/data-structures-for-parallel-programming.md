---
title: "Datové struktury pro paralelní programování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f2da3e1ecfb9018adf7827aad6a569cd057c59eb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="data-structures-for-parallel-programming"></a>Datové struktury pro paralelní programování
Rozhraní .NET Framework verze 4 zavádí několik nových typů, které jsou užitečné v paralelní programování, včetně sadu souběžných kolekce tříd, zjednodušené synchronizace primitiv a typy pro opožděné inicializace. Všechny aplikace s více vlákny kód, včetně Task Parallel Library a PLINQ můžete používat tyto typy.  
  
## <a name="concurrent-collection-classes"></a>Souběžná kolekce tříd  
 Třídy kolekce v <xref:System.Collections.Concurrent?displayProperty=nameWithType> oboru názvů zadejte vláken přidávat a odstraňovat operace, které vyhnout zámky, pokud je to možné a pomocí podrobných zamykání, kde jsou potřebné zámky. Na rozdíl od kolekcí, které byly zavedeny v rozhraní .NET Framework verze 1.0 a 2.0 nevyžaduje třídu souběžných kolekce uživatelského kódu se má provést jakékoli zámky při přistupuje k položky. Třídy souběžných kolekce může výrazně zlepšit výkon nad typy, jako <xref:System.Collections.ArrayList?displayProperty=nameWithType> a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> (s implementované uživatele uzamčení) ve scénářích, kde více vláken, přidání a odebrání položek z kolekce.  
  
 Následující tabulka uvádí nové třídy souběžných kolekce:  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|Poskytuje blokování a možnosti pro kolekce bezpečné pro přístup z více vláken, které implementují ohraničujícího <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType>. Producent vláken blok, pokud nejsou dostupné žádné sloty nebo pokud kolekce je plný. Příjemce vláken blokovat, pokud se kolekce je prázdná. Tento typ podporuje také neblokující přístup spotřebitelů a výrobců. <xref:System.Collections.Concurrent.BlockingCollection%601>lze použít jako základní třída nebo zálohování úložiště k poskytování blokování a ohraničujícího pro třídy kolekce, které podporuje <xref:System.Collections.Generic.IEnumerable%601>.|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|Implementace bezpečné pro přístup z více vláken kontejner objektů a dat, která poskytuje škálovatelné přidejte a získejte operace.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|Typ souběžných a škálovatelné slovníku.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|Fronty FIFO souběžných a škálovatelnost.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|Zásobník LIFO souběžných a škálovatelnost.|  
  
 Další informace najdete v tématu [kolekce se zabezpečenými vlákny](../../../docs/standard/collections/thread-safe/index.md).  
  
## <a name="synchronization-primitives"></a>Synchronizace primitiv  
 Nové synchronizace primitiv v <xref:System.Threading?displayProperty=nameWithType> obor názvů povolit podrobné souběžnosti a vyšší výkon vyhnout nákladné uzamčení mechanismy nalezen v kódu starší verze více vláken. Některé z nových typů, jako například <xref:System.Threading.Barrier?displayProperty=nameWithType> a <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> mít žádné svými protějšky v dřívějších verzích rozhraní .NET Framework.  
  
 Následující tabulka uvádí nové typy synchronizace:  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|Umožňuje více vláken pro práci na algoritmus paralelně tím, že poskytuje bod, kdy každý úkol signál jeho doručení a potom zablokuje, dokud se zobrazila některé nebo všechny úlohy. Další informace najdete v tématu [Barrier](../../../docs/standard/threading/barrier.md).|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|Zjednodušuje tím, že poskytuje mechanismus snadno potkávací scénáře rozvětvení a připojení. Další informace najdete v tématu [CountdownEvent](../../../docs/standard/threading/countdownevent.md).|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|Podobně jako synchronizace primitivní <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>. <xref:System.Threading.ManualResetEventSlim>je světlejšího váhy, ale lze použít pouze pro komunikace uvnitř procesy. Další informace najdete v tématu [ManualResetEvent a ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md).|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|Primitivní synchronizace, která omezuje počet vláken, které můžou současně získat přístup k prostředku nebo fond prostředků. Další informace najdete v tématu [semafor a SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|Primitivní zámku vzájemné vyloučení, která způsobuje vlákno, které se pokouší získat zámek čekat ve smyčce, nebo *typu číselník*, dobu než je jeho quantum. Ve scénářích, kde je očekávána čekání zámek být krátký <xref:System.Threading.SpinLock> nabízí vyšší výkon než jiné formy uzamčení. Další informace najdete v tématu [SpinLock](../../../docs/standard/threading/spinlock.md).|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|Malé, lightweight typ, který bude číselníku po určitou dobu a nakonec vlákno uvést do stavu čekání, pokud dojde k překročení počtu typu číselník.  Další informace najdete v tématu [objektu SpinWait](../../../docs/standard/threading/spinwait.md).|  
  
 Další informace naleznete v tématu:  
  
-   [Postupy: Použití struktury SpinLock pro synchronizaci nízké úrovně](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
-   [Postupy: synchronizace souběh operací pomocí bariéry](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="lazy-initialization-classes"></a>Opožděná inicializace třídy  
 Pomocí opožděné inicializace není přidělit paměť pro objekt, dokud nebude potřeba. Opožděná inicializace může zlepšit výkon rovnoměrně rozloží objekt přidělení napříč životnost program. Můžete povolit opožděné inicializace pro každý vlastní typ zabalení typ <xref:System.Lazy%601>.  
  
 Následující tabulka uvádí typy opožděné inicializace:  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|Poskytuje odlehčený, bezpečné pro přístup z více vláken opožděné inicializace.|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|Poskytuje hodnotu líné inicializovat na základě vlákna, každý podproces líné – vyvolání funkce inicializace.|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|Poskytuje statické metody, které nemuseli přidělit instance vyhrazené, opožděné inicializace. Místo toho používají odkazy pro zajistěte, aby byly inicializovány cíle, jako jsou přístupná.|  
  
 Další informace najdete v tématu [opožděné inicializace](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="aggregate-exceptions"></a>Agregační výjimky  
 <xref:System.AggregateException?displayProperty=nameWithType> Typ lze použít k zachycení několik výjimek, které jsou vyvolány souběžně v samostatných vláknech a vrátí je do spojovacího vlákna jako jeden výjimka. <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> typy a PLINQ použít <xref:System.AggregateException> hojně pro tento účel. Další informace najdete v tématu [NIB: postupy: zpracování výjimek vyvolaných úlohami](http://msdn.microsoft.com/library/d6c47ec8-9de9-4880-beb3-ff19ae51565d) a [postupy: zpracování výjimek v PLINQ dotazu](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Threading?displayProperty=nameWithType>  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
