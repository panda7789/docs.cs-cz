---
title: Datový paralelismus (Task Parallel Library)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, data
ms.assetid: 3f05f33f-f1da-4b16-81c2-9ceff1bef449
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19e518db75fe3e45f57cbb6fab8c5281cceb4d34
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939329"
---
# <a name="data-parallelism-task-parallel-library"></a>Datový paralelismus (Task Parallel Library)
*Datový paralelismus* odkazuje na scénáře, ve kterých je stejná operace provedena souběžně (paralelně) na prvcích ve zdrojové kolekci nebo poli. V datech paralelních operacích je zdrojová kolekce rozdělená tak, aby více vláken mohlo současně pracovat s různými segmenty.  
  
 Task Parallel Library (TPL) podporuje datový paralelismuing prostřednictvím <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> třídy. Tato třída poskytuje paralelní implementace smyček [pro](../../csharp/language-reference/keywords/for.md) a [foreach](../../csharp/language-reference/keywords/foreach-in.md) (`For` a `For Each` v Visual Basic) založené na metodách. Logiku smyčky můžete napsat pro <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> smyčku nebo <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> , která je velká, protože byste napsali sekvenční smyčku. Nemusíte vytvářet vlákna nebo pracovní položky zařazené do fronty. V základních smyčkách nemusíte přijímat zámky. TPL zpracovává veškerou práci na nízké úrovni za vás. Chcete-li získat podrobné informace o použití <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, Stáhněte si vzory dokumentů [pro paralelní programování: Porozumění a použití paralelních vzorů s .NET Framework](https://www.microsoft.com/download/details.aspx?id=19222)4. Následující příklad kódu ukazuje jednoduchou `foreach` smyčku a její paralelní ekvivalent.  
  
> [!NOTE]
> Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s lambda výrazy v C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Při spuštění paralelní smyčky aplikace TPL rozdělí zdroj dat tak, aby smyčka mohla pracovat na více částech současně. Na pozadí Plánovač úloh rozdělí úkol na základě systémových prostředků a zatížení. Pokud je to možné, Scheduler rozšíří práci mezi několika vlákny a procesory, pokud dojde k nevyrovnanému zatížení.  
  
> [!NOTE]
> Můžete také dodat vlastní rozdělovač nebo Plánovač. Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) a [plánovače úloh](xref:System.Threading.Tasks.TaskScheduler).  
  
 Obě metody <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> a mají několik přetížení, která umožňují zastavit nebo přerušit provádění smyčky, monitorovat stav smyčky v jiných vláknech, udržovat místní stav vlákna, finalizaci místních objektů vlákna, řídit stupeň souběžnosti, <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a tak dále. Pomocné typy, které umožňují tuto funkci, <xref:System.Threading.Tasks.ParallelLoopState>zahrnují <xref:System.Threading.Tasks.ParallelOptions>, <xref:System.Threading.Tasks.ParallelLoopResult>, <xref:System.Threading.CancellationToken>, a <xref:System.Threading.CancellationTokenSource>.  
  
 Další informace najdete v tématu [vzory pro paralelní programování: Porozumění a použití paralelních vzorů s .NET Framework](https://www.microsoft.com/download/details.aspx?id=19222)4.  
  
 PLINQ podporuje datový paralelismus s deklarativní syntaxí nebo dotazem, jako je syntaxe. Další informace naleznete v tématu [PARALLEL LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Napište jednoduchou paralelní smyčku. for](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|Popisuje, jak napsat <xref:System.Threading.Tasks.Parallel.For%2A> smyčku přes jakékoli pole nebo <xref:System.Collections.Generic.IEnumerable%601> indexovanou zdrojovou kolekci.|  
|[Postupy: Zápis jednoduché smyčky Parallel. ForEach](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|Popisuje, jak napsat <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčku přes jakoukoli <xref:System.Collections.Generic.IEnumerable%601> zdrojovou kolekci.|  
|[Postupy: Zastavení nebo přerušení z paralelní smyčky for](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100))|Popisuje, jak zastavit nebo přerušit paralelní smyčka, aby všechna vlákna byla informována o akci.|  
|[Postupy: Zápis Parallel. for Loop s proměnnými místními vlákny](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Popisuje, jak napsat <xref:System.Threading.Tasks.Parallel.For%2A> smyčku, ve které každé vlákno udržuje soukromou proměnnou, která není viditelná pro žádné další podprocesy, a jak synchronizovat výsledky ze všech vláken po dokončení smyčky.|  
|[Postupy: Zápis paralelní smyčky. ForEach s proměnnými místními oddíly](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)|Popisuje, jak napsat <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčku, ve které každé vlákno udržuje soukromou proměnnou, která není viditelná pro žádné další podprocesy, a jak synchronizovat výsledky ze všech vláken po dokončení smyčky.|  
|[Postupy: Zrušení smyčky Parallel. for nebo ForEach](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|Popisuje, jak zrušit paralelní smyčku pomocí<xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Postupy: Urychlení malých smyček](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|Popisuje jeden způsob, jak zrychlit provádění, když je tělo smyčky velmi malé.|  
|[Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Poskytuje přehled úlohy paralelní knihovny.|  
|[Paralelní programování](../../../docs/standard/parallel-programming/index.md)|Zavádí paralelní programování v .NET Framework.|  
  
## <a name="see-also"></a>Viz také:

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
