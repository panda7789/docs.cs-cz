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
ms.openlocfilehash: f0910ae928e94b487df5a3dfd456ee9d7c0fb7df
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587600"
---
# <a name="data-parallelism-task-parallel-library"></a>Datový paralelismus (Task Parallel Library)
*Paralelismus dat* odkazuje na scénáře, ve kterých se provádí stejná operace souběžně (to znamená paralelně) na prvky ve zdrojové kolekci nebo matici. V paralelních operacích dat je zdrojová kolekce rozdělena na oddíly tak, aby více vláken může pracovat s různými segmenty současně.  
  
 Paralelní knihovna úloh (TPL) podporuje paralelismus dat prostřednictvím třídy. <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> Tato třída poskytuje paralelní implementace [for](../../csharp/language-reference/keywords/for.md) a [foreach](../../csharp/language-reference/keywords/foreach-in.md) `For` založené `For Each` na metodách (a v jazyce Visual Basic). Napíšete logiku <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> smyčky <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pro nebo smyčky stejně jako byste napsat sekvenční smyčky. Není třeba vytvářet vlákna nebo fronty pracovních položek. V základních smyčkách nemusíte užívat zámky. TPL zvládá veškerou práci na nízké úrovni za vás. Podrobné informace o použití <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> aplikace <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>a , stáhněte dokument [Vzory pro paralelní programování: Porozumění a použití paralelních vzorů pomocí rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222). Následující příklad kódu ukazuje `foreach` jednoduchou smyčku a její paralelní ekvivalent.  
  
> [!NOTE]
> Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, naleznete [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Při spuštění paralelní smyčky TPL rozdělí zdroj dat tak, aby smyčka může pracovat na více částí současně. Na pozadí plánovač úloh rozdělí úlohu na základě systémových prostředků a zatížení. Pokud je to možné, plánovač redistribuuje práci mezi více vlákny a procesory, pokud se pracovní vytížení stane nevyváženým.  
  
> [!NOTE]
> Můžete také zadat vlastní rozdělovač nebo plánovač. Další informace naleznete [v tématu Vlastní rozdělovače pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) a [plánovače úloh](xref:System.Threading.Tasks.TaskScheduler).  
  
 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> A metody <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> mají několik přetížení, které umožňují zastavit nebo přerušit spuštění smyčky, sledovat stav smyčky v jiných vláknech, udržovat místní stav vlákna, dokončit objekty místní podproces, řídit stupeň souběžnosti a tak dále. Mezi pomocné typy, které <xref:System.Threading.Tasks.ParallelLoopState>tuto <xref:System.Threading.Tasks.ParallelOptions> <xref:System.Threading.Tasks.ParallelLoopResult>funkci <xref:System.Threading.CancellationToken>umožňují, patří , , , a <xref:System.Threading.CancellationTokenSource>.  
  
 Další informace naleznete [v tématu Vzory pro paralelní programování: Principy a použití paralelních vzorů s rozhraním .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222).  
  
 Paralelismus dat s deklarativní syntaxí nebo syntaxí podobný dotazu je podporován plinq. Další informace naleznete [v tématu Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Postupy: Zápis jednoduché smyčky Parallel.For](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|Popisuje, jak napsat <xref:System.Threading.Tasks.Parallel.For%2A> smyčku přes <xref:System.Collections.Generic.IEnumerable%601> libovolné pole nebo indexovatelné zdrojové kolekce.|  
|[Postupy: Zápis jednoduché smyčky Parallel.ForEach](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|Popisuje, jak napsat <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčku přes všechny <xref:System.Collections.Generic.IEnumerable%601> zdrojové kolekce.|  
|[Postup: Zastavení nebo přerušení z parallel.for smyčky](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100))|Popisuje, jak zastavit nebo přerušit z paralelní smyčky tak, aby všechny podprocesy jsou informováni o akci.|  
|[Postupy: Zápis smyčky Parallel.For pomocí proměnných v místním vláknu](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Popisuje, jak napsat <xref:System.Threading.Tasks.Parallel.For%2A> smyčku, ve kterém každé vlákno udržuje soukromou proměnnou, která není viditelná pro žádná jiná vlákna, a jak synchronizovat výsledky ze všech vláken po dokončení smyčky.|  
|[Postupy: Zápis smyčky Parallel.ForEach pomocí proměnných v místním oddílu](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)|Popisuje, jak napsat <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčku, ve kterém každé vlákno udržuje soukromou proměnnou, která není viditelná pro žádná jiná vlákna, a jak synchronizovat výsledky ze všech vláken po dokončení smyčky.|  
|[Postupy: Zrušení smyček Parallel.For nebo ForEach](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|Popisuje, jak zrušit paralelní smyčku pomocí<xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Postupy: Zrychlení malých smyček](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|Popisuje jeden způsob, jak urychlit provádění, když tělo smyčky je velmi malý.|  
|[Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Obsahuje přehled paralelní knihovny úloh.|  
|[Paralelní programování](../../../docs/standard/parallel-programming/index.md)|Zavádí paralelní programování v rozhraní .NET Framework.|  
  
## <a name="see-also"></a>Viz také

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
