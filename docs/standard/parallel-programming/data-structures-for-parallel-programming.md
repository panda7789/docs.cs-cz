---
title: Datové struktury pro paralelní programování
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
ms.openlocfilehash: f9c130b73044440f24b7b8bbebe9527490a165c1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288521"
---
# <a name="data-structures-for-parallel-programming"></a>Datové struktury pro paralelní programování
.NET Framework verze 4 zavádí několik nových typů, které jsou užitečné v paralelním programování, včetně sady souběžných tříd kolekcí, zjednodušené synchronizace primitiv a typů pro opožděnou inicializaci. Tyto typy můžete použít s libovolným kódem aplikace s více vlákny, včetně Task Parallel Library a PLINQ.  
  
## <a name="concurrent-collection-classes"></a>Třídy souběžných kolekcí  
 Třídy kolekce v <xref:System.Collections.Concurrent?displayProperty=nameWithType> oboru názvů poskytují operace přidání a odebrání bezpečné pro přístup z více vláken, které zabraňují uzamčení bez ohledu na to, kde je to možné, a použití jemně odstupňovaného zamykání, kde jsou nutná zámky Na rozdíl od kolekcí, které byly představeny v .NET Framework verzích 1,0 a 2,0, třída souběžného shromažďování nevyžaduje, aby při přístupu k položkám převzala kód uživatele. Třídy souběžných kolekcí můžou významně zlepšit výkon nad typy, jako jsou <xref:System.Collections.ArrayList?displayProperty=nameWithType> a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> (s uživatelem implementovaným zámkem) ve scénářích, kdy více vláken přidává a odebírá položky z kolekce.  
  
 Následující tabulka uvádí nové třídy souběžných kolekcí:  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|Poskytuje blokující a ohraničování možností pro kolekce bezpečné pro přístup z více vláken, které implementují <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> . Vlákna producenta zablokují, pokud nejsou k dispozici žádné sloty nebo pokud je kolekce plná. Vlákna příjemce jsou blokována, pokud je kolekce prázdná. Tento typ také podporuje neblokující přístup uživatelů a výrobců. <xref:System.Collections.Concurrent.BlockingCollection%601>dá se použít jako základní třída nebo záložní úložiště k poskytnutí blokování a vázání pro libovolnou třídu kolekce, která podporuje <xref:System.Collections.Generic.IEnumerable%601> .|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|Implementace kontejneru bezpečná pro přístup z více vláken, která poskytuje škálovatelné operace přidání a získání.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|Souběžný a škálovatelný typ slovníku.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|Souběžná a škálovatelná fronta FIFO.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|Souběžný a škálovatelný zásobník LIFO.|  
  
 Další informace najdete v tématu [kolekce bezpečné](../collections/thread-safe/index.md)pro přístup z více vláken.  
  
## <a name="synchronization-primitives"></a>Synchronizace primitiv  
 Nové synchronizační primitiva v <xref:System.Threading?displayProperty=nameWithType> oboru názvů umožňují jemně odstupňovaný a rychlejší výkon tím, že v kódu s více vlákny vyloučí nákladný mechanizmy zámků. Některé nové typy, například <xref:System.Threading.Barrier?displayProperty=nameWithType> a <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> nemají žádné protějšky v dřívějších verzích .NET Framework.  
  
 Následující tabulka uvádí nové typy synchronizace:  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|Umožňuje více vláknům souběžně pracovat s algoritmem tím, že poskytuje bod, ve kterém každý úkol může signalizovat doručení a pak zablokovat, dokud nebudou přijaty některé nebo všechny úlohy. Další informace najdete v tématu [bariéra](../threading/barrier.md).|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|Zjednodušuje rozvětvení a spojování scénářů poskytnutím jednoduchého mechanizmu Rendezvous. Další informace najdete v tématu [CountdownEvent](../threading/countdownevent.md).|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|Primitiva synchronizace podobná <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> . <xref:System.Threading.ManualResetEventSlim>je světlejší-váha, ale dá se použít jenom pro komunikaci uvnitř procesu.|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|Primitiva synchronizace, která omezuje počet vláken, která můžou souběžně přistupovat k prostředku nebo k fondu prostředků. Další informace najdete v tématu [semafor a SemaphoreSlim](../threading/semaphore-and-semaphoreslim.md).|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|Primitiva vzájemného zámku pro vyloučení, která způsobí, že vlákno, které se pokouší získat zámek, čeká ve smyčce nebo *číselníku*po určitou dobu před vyřazením jeho nestavů. Ve scénářích, kdy se očekává, že je čekání na zámek krátké, <xref:System.Threading.SpinLock> nabízí lepší výkon než jiné formy zamykání. Další informace najdete v tématu [struktuře SpinLock](../threading/spinlock.md).|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|Malý, lehký typ, který se po určitou dobu vytočí a nakonec vloží vlákno do čekacího stavu, pokud je překročený počet číselníku.  Další informace najdete v tématu [objektu SpinWait](../threading/spinwait.md).|  
  
 Další informace naleznete v tématu:  
  
- [Postupy: Použití struktury SpinLock pro synchronizaci nízké úrovně](../threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
- [Postupy: synchronizace souběžných operací s bariérou](../threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="lazy-initialization-classes"></a>Třídy opožděné inicializace  
 V případě opožděné inicializace není paměť pro objekt přidělena, dokud není nutné. Opožděná inicializace může zvýšit výkon rozšířením přidělení objektů rovnoměrně po celou dobu životnosti programu. Můžete povolit opožděnou inicializaci pro libovolný vlastní typ vybalením typu <xref:System.Lazy%601> .  
  
 V následující tabulce jsou uvedeny typy opožděné inicializace:  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|Poskytuje odlehčenou inicializaci bezpečnou pro přístup z více vláken.|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|Poskytuje laxně vytvářená inicializovaných hodnot pro každé vlákno, přičemž každé vlákno laxně vytvářená vyvolá inicializační funkci.|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|Poskytuje statické metody, které zabraňují nutnosti přidělit vyhrazenou instanci opožděné inicializace. Místo toho používají odkazy, aby bylo zajištěno, že cíle byly inicializovány při jejich použití.|  
  
 Další informace naleznete v tématu [opožděná inicializace](../../framework/performance/lazy-initialization.md).  
  
## <a name="aggregate-exceptions"></a>Agregované výjimky  
 <xref:System.AggregateException?displayProperty=nameWithType>Typ lze použít k zachycení více výjimek, které jsou vyvolány souběžně v samostatných vláknech a vrátí je do spojovacího vlákna jako jediná výjimka. <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>Typy a <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> a PLINQ používají <xref:System.AggregateException> pro tento účel rozsáhlou práci. Další informace naleznete v tématu [zpracování výjimek](exception-handling-task-parallel-library.md) a [Postupy: zpracování výjimek v dotazu PLINQ](how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- <xref:System.Threading?displayProperty=nameWithType>
- [Paralelní programování](index.md)
