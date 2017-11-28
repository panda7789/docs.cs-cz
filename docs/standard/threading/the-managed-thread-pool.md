---
title: "Spravovaný fond vláken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- thread pooling [.NET Framework]
- thread pools [.NET Framework]
- threading [.NET Framework], thread pool
- threading [.NET Framework], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 38032fccce1a8f6f7cbcb3bbd3d3f9d008a74141
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="the-managed-thread-pool"></a>Spravovaný fond vláken
<xref:System.Threading.ThreadPool> Třída poskytuje vaší aplikace pomocí fond pracovních vláken, které jsou spravovány nástrojem systému, což umožňuje soustředit se jenom na úlohy aplikace a nikoli vláken správy. Pokud máte krátké úlohy, které vyžadují zpracování na pozadí, spravovaný fond vláken je snadný způsob, jak využít výhod více vláken. Například počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] můžete vytvořit <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objekty, které asynchronní zpracovávat podprocesy z fondu podprocesů.  
  
> [!NOTE]
>  Počínaje [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], propustnost fondu vláken je výrazně zlepšila v tři klíčové oblasti, které byly identifikovány jako kritická místa v předchozích verzích [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]: řazení do fronty úloh, odeslání podprocesy z fondu podprocesů a odeslání vstupně-výstupních operací dokončení vláken. Chcete-li používat tuto funkci, by měl cíle vaší aplikace [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] nebo novější.  
  
 Pro úlohy na pozadí, které zajišťují interakci s uživatelským rozhraním, rozhraní .NET Framework verze 2.0 také poskytuje <xref:System.ComponentModel.BackgroundWorker> třídy, která komunikuje pomocí událostí vyvolaných ve vláknu uživatelského rozhraní.  
  
 Rozhraní .NET Framework používá podprocesy z fondu podprocesů mnoho důvodů, včetně dokončení asynchronní vstupně-výstupních operací, zpětná volání časovače, zaregistrovaný Počkejte, než operace, asynchronní metoda volá použití delegátů, a <xref:System.Net> připojení soketu.  
  
## <a name="when-not-to-use-thread-pool-threads"></a>Kdy nepoužívat podprocesy z fondu podprocesů  
 Existuje několik situací, ve kterých je vhodné vytvořit a spravovat vlastní vláken místo použití podprocesy z fondu podprocesů:  
  
-   Vyžadujete, aby vlákna popředí.  
  
-   Vyžadujete, aby vlákno konkrétní prioritu.  
  
-   Máte úkoly, které způsobí vlákno blokování pro dlouhou dobu. Fond vláken má maximální počet vláken, takže Velký počet blokovaných podprocesy z fondu podprocesů může úlohy zabránit ve spuštění.  
  
-   Je nutné umístit do single-threaded apartment vláken. Všechny <xref:System.Threading.ThreadPool> vláken jsou ve více vláken typu apartment.  
  
-   Musíte mít stabilní identita spojená s vlákno nebo vyhradit vlákno k úloze.  
  
## <a name="thread-pool-characteristics"></a>Vlastnosti fondu vláken  
 Podprocesy z fondu podprocesů jsou vlákna na pozadí. V tématu [na popředí a vlákna na pozadí](../../../docs/standard/threading/foreground-and-background-threads.md). Každé vlákno používá výchozí velikost zásobníku, běží na výchozí prioritu a je ve více vláken typu apartment.  
  
 Není k dispozici pouze jedno vlákno fondu podle procesu.  
  
### <a name="exceptions-in-thread-pool-threads"></a>Výjimky v podprocesy z fondu podprocesů  
 Nezpracované výjimky na podprocesy z fondu podprocesů ukončit proces. Existují tři výjimky pro toto pravidlo:  
  
-   A <xref:System.Threading.ThreadAbortException> je vyvolána v podprocesu fondu vláken, protože <xref:System.Threading.Thread.Abort%2A> byla volána.  
  
-   <xref:System.AppDomainUnloadedException> Je vyvolána v podprocesu fondu vláken, protože odpojení domény aplikace.  
  
-   Modul common language runtime nebo hostitelský proces se ukončuje vlákno.  
  
 Další informace najdete v tématu [výjimky ve spravovaných vláknech](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 1.0 a 1.1 modul common language runtime bezobslužně traps neošetřenými výjimkami v podprocesy z fondu podprocesů. To může být poškozený stav aplikace a nakonec způsobit, že aplikace přestane reagovat, což může být velmi obtížné ladění.  
  
### <a name="maximum-number-of-thread-pool-threads"></a>Maximální počet vláken fondu vláken  
 Počet operací, které lze zařadit do fronty pro fond vláken je omezena pouze dostupná paměť; fond vláken však omezuje počet vláken, které mohou být aktivní v procesu současně. Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], výchozí velikost fondu vláken pro proces závisí na několika faktorech, jako je například velikost virtuálního adresového prostoru. Proces můžete volat <xref:System.Threading.ThreadPool.GetMaxThreads%2A> metoda k určení počtu vláken.  
  
 Maximální počet vláken můžete řídit pomocí <xref:System.Threading.ThreadPool.GetMaxThreads%2A> a <xref:System.Threading.ThreadPool.SetMaxThreads%2A> metody.  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 1.0 a 1.1 nelze nastavit velikost fondu vláken ze spravovaného kódu. Kód, který je hostitelem modul common language runtime můžete nastavit na velikost pomocí `CorSetMaxThreads`, definované v mscoree.h.  
  
### <a name="thread-pool-minimums"></a>Minimálních fondu vláken  
 Fond vláken poskytuje nové pracovních vláken nebo vláken dokončení vstupně-výstupních operací na vyžádání, dokud nedosáhne zadané minimálně pro každou kategorii. Můžete použít <xref:System.Threading.ThreadPool.GetMinThreads%2A> metoda získat tyto minimální hodnoty.  
  
> [!NOTE]
>  Při malém vyžádání skutečný počet podprocesy z fondu podprocesů můžete klesnou pod minimální hodnoty.  
  
 Když je dosaženo minimální, fondu vláken můžete vytvořit další vlákna nebo počkejte na dokončení některých úloh. Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], fondu vláken vytváří a ukončuje pracovních vláken k optimalizaci propustnosti, která je definována jako počet úloh, která dokončí za časovou jednotku. Příliš málo vláken nemusí využívají optimální dostupné prostředky, zatímco příliš mnoho vláken může zhoršit sporu prostředků.  
  
> [!CAUTION]
>  Můžete použít <xref:System.Threading.ThreadPool.SetMinThreads%2A> metoda zvýšit minimální počet nečinných vláken. Zbytečně zvýšení tyto hodnoty však může způsobit problémy s výkonem. Pokud ve stejnou dobu příliš mnoho úloh, spusťte všechny z nich může se zobrazí za pomalé. Ve většině případů budou líp fungovat fondu vláken se vlastní algoritmus pro přidělování vláken.  
  
## <a name="skipping-security-checks"></a>Přeskočení kontroly zabezpečení  
 Fond vláken také poskytuje <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> a <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> metody. Tyto metody používáte jenom v případě, že jste si jisti, že zásobník volajícího je důležité pro všechny kontroly zabezpečení prováděné během provádění úlohy ve frontě. <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>a <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> obě zaznamenat volajícího zásobníku, která sloučí zásobník vlákno fondu vláken zahájení vlákno k provedení úlohy. Pokud kontrola zabezpečení se požaduje, musí být kontrolované celý zásobník. I když je kontrola poskytuje zabezpečení, je také nákladů na výkon.  
  
## <a name="using-the-thread-pool"></a>Použití fondu vláken  
 Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], nejjednodušší způsob, jak používat fond vláken je použití [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md). Ve výchozím nastavení, jako jsou typy paralelní knihovny <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> podprocesy z fondu podprocesů použít ke spuštění úlohy. Můžete také použít fondu vláken voláním <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> ze spravovaného kódu (nebo `CorQueueUserWorkItem` z nespravovaného kódu) a předání <xref:System.Threading.WaitCallback> delegovat představující metodu, která provádí úkol. Další způsob použití fondu vláken je zařadit do fronty pracovních položek, které souvisí s operací počkejte pomocí <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> metoda a předávání <xref:System.Threading.WaitHandle> , když signál, nebo po vypršení časového limitu, volá metodu reprezentovanou <xref:System.Threading.WaitOrTimerCallback> delegovat. Podprocesy z fondu podprocesů slouží k vyvolání metody zpětného volání.  
  
## <a name="threadpool-examples"></a>Příklady fondu  
 Příklady kódu v této části ukazují fondu vláken pomocí <xref:System.Threading.Tasks.Task> třídy, <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> metoda a <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> metoda.  
  
-   [Provádění asynchronní úlohy s Task Parallel Library](#TaskParallelLibrary)  
  
-   [Provádění kódu asynchronně s QueueUserWorkItem](#ExecuteCodeWithQUWI)  
  
-   [Poskytuje Data úlohy pro QueueUserWorkItem](#TaskDataForQUWI)  
  
-   [Pomocí funkce RegisterWaitForSingleObject](#RegisterWaitForSingleObject)  
  
<a name="TaskParallelLibrary"></a>   
### <a name="executing-asynchronous-tasks-with-the-task-parallel-library"></a>Provádění asynchronní úlohy s Task Parallel Library  
 Následující příklad ukazuje, jak vytvořit a použít <xref:System.Threading.Tasks.Task> objekt voláním <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metoda. Pro příklad, který používá <xref:System.Threading.Tasks.Task%601> třída vrácení hodnoty z asynchronní úlohu, najdete v článku [postupy: vrácení hodnoty z úlohy](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).  
  
 [!code-csharp[System.Threading.Tasks.Task#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.task/cs/startnew.cs#01)]
 [!code-vb[System.Threading.Tasks.Task#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.task/vb/startnew.vb#01)]  
  
<a name="ExecuteCodeWithQUWI"></a>   
### <a name="executing-code-asynchronously-with-queueuserworkitem"></a>Provádění kódu asynchronně s QueueUserWorkItem  
 V následujícím příkladu fronty velmi jednoduché úlohy, která je reprezentována `ThreadProc` metodu, pomocí <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metoda.  
  
 [!code-cpp[Conceptual.ThreadPool#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.ThreadPool#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source1.cs#1)]
 [!code-vb[Conceptual.ThreadPool#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source1.vb#1)]  
  
<a name="TaskDataForQUWI"></a>   
### <a name="supplying-task-data-for-queueuserworkitem"></a>Poskytuje Data úlohy pro QueueUserWorkItem  
 Následující příklad kódu používá <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metoda úlohu ve frontě a zadat data pro úlohu.  
  
 [!code-cpp[Conceptual.ThreadPool#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.ThreadPool#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source2.cs#2)]
 [!code-vb[Conceptual.ThreadPool#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source2.vb#2)]  
  
<a name="RegisterWaitForSingleObject"></a>   
### <a name="using-registerwaitforsingleobject"></a>Pomocí funkce RegisterWaitForSingleObject  
 Následující příklad ukazuje několik vláken funkcí.  
  
-   Služba Řízení front úlohu pro spuštění s <xref:System.Threading.ThreadPool> vláken, s <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> metoda.  
  
-   Signalizace úlohu provést, s <xref:System.Threading.AutoResetEvent>. V tématu [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md).  
  
-   Zpracování vypršení časových limitů a signály s <xref:System.Threading.WaitOrTimerCallback> delegovat.  
  
-   Zrušení úlohu ve frontě s <xref:System.Threading.RegisteredWaitHandle>.  
  
 [!code-cpp[Conceptual.ThreadPool#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.ThreadPool#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source3.cs#3)]
 [!code-vb[Conceptual.ThreadPool#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.ThreadPool>  
 <xref:System.Threading.Tasks.Task>  
 <xref:System.Threading.Tasks.Task%601>  
 [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [Postupy: vrácení hodnoty z úlohy](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)  
 [Dělení na vlákna objektů a funkcí](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Vlákna a dělení na vlákna](../../../docs/standard/threading/threads-and-threading.md)  
 [Asynchronní I/O soubory](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [Časovače](../../../docs/standard/threading/timers.md)
