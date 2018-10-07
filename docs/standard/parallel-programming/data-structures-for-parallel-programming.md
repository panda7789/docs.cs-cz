---
title: Datové struktury pro paralelní programování
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6453e9983086dcb5b97ec134db9d74160d7a47cf
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836469"
---
# <a name="data-structures-for-parallel-programming"></a>Datové struktury pro paralelní programování
Rozhraní .NET Framework verze 4 přináší několik nových typů, které jsou užitečné pro paralelní programování, včetně sady souběžných kolekcí tříd, zjednodušené synchronizace primitiv a typy pro opožděnou inicializaci. Můžete použít tyto typy s jakýmkoli jiným kódem aplikace s více vlákny, včetně Task Parallel Library a PLINQ.  
  
## <a name="concurrent-collection-classes"></a>Souběžné kolekce tříd  
 Kolekce tříd v <xref:System.Collections.Concurrent?displayProperty=nameWithType> obor názvů poskytují bezpečné pro vlákna přidávat a odebírat operace, které se vyhnout uzamčení, kdykoli je to možné a použití jemně uzamčení, pokud jsou potřebné zámky. Na rozdíl od kolekcí, které byly zavedeny v rozhraní .NET Framework verze 1.0 a 2.0 nevyžaduje třídu souběžných kolekcích uživatelský kód pro žádné zámky při přístupu ke položky. Souběžné kolekce tříd může výrazně zlepšit výkon typy, jako <xref:System.Collections.ArrayList?displayProperty=nameWithType> a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> (s implementované uživatele uzamčení) v situacích, kdy více vláken, přidání a odebrání položek z kolekce.  
  
 V následující tabulce jsou uvedeny nové třídy souběžných kolekcí:  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|Poskytuje blokování a možnosti pro kolekce bezpečné pro vlákna, které implementují ohraničující <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType>. Výrobce vlákna blokovat, pokud nejsou dostupné žádné sloty nebo pokud kolekce je plná. Příjemce vlákna blokovat, pokud kolekce je prázdná. Tento typ podporuje také neblokující přístup tak, že příjemci a výrobci. <xref:System.Collections.Concurrent.BlockingCollection%601> lze jej použít jako základní třída nebo záložní úložiště k poskytování blokování a ohraničující pro třídy kolekce, které podporuje <xref:System.Collections.Generic.IEnumerable%601>.|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|Implementace bezpečné pro vlákna kontejner objektů a dat, která poskytuje škálovatelné přidat a operacemi get.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|Typ slovníku souběžného a škálovatelná.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|Fronty FIFO souběžného a škálovatelná.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|Zásobník LIFO souběžného a škálovatelná.|  
  
 Další informace najdete v tématu [kolekce bezpečné pro vlákna](../../../docs/standard/collections/thread-safe/index.md).  
  
## <a name="synchronization-primitives"></a>Synchronizace primitiv  
 Nová synchronizace primitiv v <xref:System.Threading?displayProperty=nameWithType> obor názvů povolit jemné souběžnosti a rychlejší výkon nákladné zamykání mechanismy ve starší verzi multithreading kódu se našel se vyhnout. Některé z nových typů, jako například <xref:System.Threading.Barrier?displayProperty=nameWithType> a <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> mít žádné protějšky v dřívějších verzích rozhraní .NET Framework.  
  
 V následující tabulce jsou uvedeny nové typy synchronizace:  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|Umožňuje více vláken pro práci na algoritmus paralelně tím, že poskytuje bod, ve kterém každý úkol signalizuje, že jeho doručení a potom blokovat, dokud se objevit některé nebo všechny úlohy. Další informace najdete v tématu [bariéry](../../../docs/standard/threading/barrier.md).|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|Tím, že poskytuje mechanismus pro snadné potkávací zjednodušuje scénáře rozvětvení a spojení. Další informace najdete v tématu [CountdownEvent](../../../docs/standard/threading/countdownevent.md).|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|Synchronizace primitiv podobný <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>. <xref:System.Threading.ManualResetEventSlim> je míň náročné, ale jde použít jenom pro komunikace uvnitř procesu. Další informace najdete v tématu [ManualResetEvent a ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md).|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|Synchronizace primitiv, která omezuje počet vláken, která může současně přistupovat k prostředku nebo fond prostředků. Další informace najdete v tématu [Semaphore a SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|Vzájemné vyloučení zámek jednoduchého typu, který způsobí, že vlákno, které se pokouší získat zámek čekat ve smyčce, nebo *typu číselník*, dobu před tím, než získávání jeho kvantové doby. Ve scénářích, kde je očekávána čekání na uzamčení krátkodobé <xref:System.Threading.SpinLock> nabízí vyšší výkon než jiné formy uzamčení. Další informace najdete v tématu [SpinLock](../../../docs/standard/threading/spinlock.md).|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|Malé, jednoduchý typ, který bude aktivovat určitou dobu a nakonec umístit vlákno do stavu čekání, pokud je překročen počet typu číselník.  Další informace najdete v tématu [objektu SpinWait](../../../docs/standard/threading/spinwait.md).|  
  
 Další informace naleznete v tématu:  
  
-   [Postupy: Použití struktury SpinLock pro synchronizaci nízké úrovně](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
-   [Postupy: synchronizace souběh operací pomocí bariéry](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="lazy-initialization-classes"></a>Opožděná inicializace třídy  
 Pomocí opožděné inicializace není přidělena paměť pro objekt, dokud nebude potřeba. Opožděná inicializace lze vylepšit výkon rovnoměrně rozprostírá přidělení objektů na dobu životnosti programu. Můžete povolit pro všechny vlastní typy opožděná inicializace obalením typ <xref:System.Lazy%601>.  
  
 V následující tabulce jsou uvedeny typy opožděná inicializace:  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|Poskytuje odlehčený, bezpečné pro vlákna opožděné inicializace.|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|Poskytuje hodnotu laxně inicializovaný na základě vlákno každý podproces laxně – vyvolání funkce inicializace.|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|Poskytuje statické metody, které se vyhnuli nutnosti přidělit vyhrazené instanci opožděné inicializace. Místo toho používají odkazy k Ujistěte se, že cíle jsou inicializované, jako jsou přístupné.|  
  
 Další informace najdete v tématu [opožděné inicializace](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="aggregate-exceptions"></a>Agregační výjimky  
 <xref:System.AggregateException?displayProperty=nameWithType> Typ lze použít k zachycení výjimky, které jsou vyvolány souběžně v samostatných vláknech a vrátit je do spojovacího vlákna jako jednu výjimku. <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> typy a PLINQ používat <xref:System.AggregateException> výrazně pro tento účel. Další informace najdete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md) a [postupy: zpracování výjimek v dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- <xref:System.Threading?displayProperty=nameWithType>  
- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
