---
title: Datové struktury pro paralelní programování
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
ms.openlocfilehash: a2271feae78100940b4ecac3c42c9bfefa7e1769
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123141"
---
# <a name="data-structures-for-parallel-programming"></a>Datové struktury pro paralelní programování
Rozhraní .NET Framework verze 4 zavádí několik nových typů, které jsou užitečné v paralelníprogramování, včetně sady tříd souběžných kolekcí, zjednodušené synchronizace primitiv a typy pro opožděné inicializace. Tyto typy můžete použít s libovolným vícevláknovým kódem aplikace, včetně paralelní knihovny úloh a PLINQ.  
  
## <a name="concurrent-collection-classes"></a>Třídy souběžných kolekcí  
 Třídy kolekce <xref:System.Collections.Concurrent?displayProperty=nameWithType> v oboru názvů poskytují operace přidání a odebrání bezpečných pro přístup z více vláken, které se vyhýbají uzamčení, kdykoli je to možné, a používají jemně odstupňované zamykání tam, kde jsou nezbytné zámky. Na rozdíl od kolekcí, které byly zavedeny v rozhraní .NET Framework verze 1.0 a 2.0, souběžné třídy kolekce nevyžaduje uživatelský kód, aby všechny zámky při přístupu k položky. Třídy souběžné kolekce můžete výrazně zlepšit <xref:System.Collections.ArrayList?displayProperty=nameWithType> <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> výkon oproti typům, jako je například a (s uživatelem implementované uzamčení) ve scénářích, kde více vláken přidat a odebrat položky z kolekce.  
  
 V následující tabulce jsou uvedeny nové třídy souběžné kolekce:  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|Poskytuje možnosti blokování a ohraničování <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType>pro kolekce bezpečné pro přístup z více vláken, které implementují . Podprocesy výrobce blokovat, pokud nejsou k dispozici žádné sloty nebo pokud je kolekce plná. Spotřebitelské podprocesy blokovat, pokud je kolekce prázdná. Tento typ také podporuje neblokující přístup spotřebitelů a výrobců. <xref:System.Collections.Concurrent.BlockingCollection%601>lze použít jako základní třídy nebo záložní úložiště poskytnout blokování a <xref:System.Collections.Generic.IEnumerable%601>ohraničování pro všechny třídy kolekce, která podporuje .|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|Implementace vaku bezpečné pro přístup z více vláken, která poskytuje škálovatelné operace pro přidání a získání.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|Souběžný a škálovatelný typ slovníku.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|Souběžná a škálovatelná fronta FIFO.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|Souběžný a škálovatelný zásobník LIFO.|  
  
 Další informace naleznete v [tématu Thread-Safe Collections](../../../docs/standard/collections/thread-safe/index.md).  
  
## <a name="synchronization-primitives"></a>Základní synchronizace  
 Nová synchronizace primitiv v oboru <xref:System.Threading?displayProperty=nameWithType> názvů umožňují jemně odstupňované souběžnosti a rychlejší výkon tím, že se zabrání nákladné zamykání mechanismy nalezené ve starším kódu více vláken. Některé nové typy, <xref:System.Threading.Barrier?displayProperty=nameWithType> například <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> a nemají žádné protějšky v dřívějších verzích rozhraní .NET Framework.  
  
 V následující tabulce jsou uvedeny nové typy synchronizace:  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|Umožňuje více podprocesů pracovat na algoritmu paralelně tím, že poskytuje bod, ve kterém každý úkol může signalizovat jeho příchod a pak blokovat, dokud některé nebo všechny úkoly dorazily. Další informace naleznete v tématu [Barrier](../../../docs/standard/threading/barrier.md).|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|Zjednodušuje scénáře rozřezává a spojuje tím, že poskytuje snadný mechanismus setkání. Další informace naleznete v tématu [CountdownEvent](../../../docs/standard/threading/countdownevent.md).|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|Synchronizace primitivní podobné <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>. <xref:System.Threading.ManualResetEventSlim>je lehčí, ale lze jej použít pouze pro vnitroprocesovou komunikaci.|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|Synchronizační primitiv, který omezuje počet podprocesů, které mohou současně přistupovat k prostředku nebo fondu prostředků. Další informace naleznete [v tématech Semafor a SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|Vzájemné vyloučení zámek primitivní, který způsobí, že podproces, který se pokouší získat zámek čekat ve smyčce nebo *spin*, po určitou dobu před získáním jeho kvantové. Ve scénářích, kde se očekává, že <xref:System.Threading.SpinLock> čekání na zámek bude krátká, nabízí lepší výkon než jiné formy uzamčení. Další informace naleznete v tématu [SpinLock](../../../docs/standard/threading/spinlock.md).|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|Malý, lehký typ, který se bude otáčet po určitou dobu a nakonec uvede vlákno do stavu čekání, pokud je překročen počet odstřeďování.  Další informace naleznete v tématu [SpinWait](../../../docs/standard/threading/spinwait.md).|  
  
 Další informace naleznete v tématu:  
  
- [Postupy: Použití struktury SpinLock pro synchronizaci nízké úrovně](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
- [Postup: Synchronizace souběžných operací s bariérou](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="lazy-initialization-classes"></a>Opožděné inicializační třídy  
 Při opožděné inicializaci není paměť pro objekt přidělena, dokud není potřeba. Opožděná inicializace může zlepšit výkon rozložením přidělení objektů rovnoměrně po celou dobu životnosti programu. Opožděnou inicializaci pro libovolný vlastní <xref:System.Lazy%601>typ můžete povolit obtékáním typu .  
  
 V následující tabulce jsou uvedeny typy opožděné inicializace:  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|Poskytuje zjednodušenou, zřetězenou inicializaci.|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|Poskytuje líně inicializovanou hodnotu pro jednotlivé vlákno, přičemž každé vlákno se líně odvolává na funkci inicializace.|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|Poskytuje statické metody, které se vyhýbají nutnosti přidělit vyhrazenou instanci opožděné inicializace. Místo toho používají odkazy k zajištění cíle byly inicializovány jako jsou přístupné.|  
  
 Další informace naleznete [v tématu Opožděná inicializace](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="aggregate-exceptions"></a>Agregační výjimky  
 Typ <xref:System.AggregateException?displayProperty=nameWithType> lze použít k zachycení více výjimek, které jsou vyvolány současně v samostatných vláknech a vrátit je do spojovacího vlákna jako jednu výjimku. Typy <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> a a PLINQ používají <xref:System.AggregateException> značně pro tento účel. Další informace naleznete v [tématu Zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md) a [postup: Zpracování výjimek v plinq dotazu](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- <xref:System.Threading?displayProperty=nameWithType>
- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
