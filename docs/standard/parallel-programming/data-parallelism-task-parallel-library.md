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
ms.openlocfilehash: 72696a41cd3b71f47fdcf43e4ece70ebeb7d34d1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123162"
---
# <a name="data-parallelism-task-parallel-library"></a>Datový paralelismus (Task Parallel Library)
*Datový paralelismus* odkazuje na scénáře, ve kterých je stejná operace provedena souběžně (paralelně) na prvcích ve zdrojové kolekci nebo poli. V datech paralelních operacích je zdrojová kolekce rozdělená tak, aby více vláken mohlo současně pracovat s různými segmenty.  
  
 Task Parallel Library (TPL) podporuje datový paralelismuing prostřednictvím třídy <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>. Tato třída poskytuje paralelní implementace smyčky [for](../../csharp/language-reference/keywords/for.md) a [foreach](../../csharp/language-reference/keywords/foreach-in.md) (`For` a `For Each` v Visual Basic). Zapisujete logiku smyčky pro <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> nebo smyčku <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, která je velká, protože byste napsali sekvenční smyčku. Nemusíte vytvářet vlákna nebo pracovní položky zařazené do fronty. V základních smyčkách nemusíte přijímat zámky. TPL zpracovává veškerou práci na nízké úrovni za vás. Chcete-li získat podrobné informace o použití <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, Stáhněte si vzor dokumentu [pro paralelní programování: porozumění a použití paralelních vzorů s .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222). Následující příklad kódu ukazuje jednoduchou smyčku `foreach` a její paralelní ekvivalent.  
  
> [!NOTE]
> Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s lambda výrazy v C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Při spuštění paralelní smyčky aplikace TPL rozdělí zdroj dat tak, aby smyčka mohla pracovat na více částech současně. Na pozadí Plánovač úloh rozdělí úkol na základě systémových prostředků a zatížení. Pokud je to možné, Scheduler rozšíří práci mezi několika vlákny a procesory, pokud dojde k nevyrovnanému zatížení.  
  
> [!NOTE]
> Můžete také dodat vlastní rozdělovač nebo Plánovač. Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) a [plánovače úloh](xref:System.Threading.Tasks.TaskScheduler).  
  
 Metody <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> mají několik přetížení, která umožňují zastavit nebo přerušit provádění smyčky, monitorovat stav smyčky v jiných vláknech, udržovat místní stav vlákna, finalizovat místní objekty vlákna, řídit stupeň souběžnosti a tak dále. Mezi pomocné typy, které tuto funkci povolují, patří <xref:System.Threading.Tasks.ParallelLoopState>, <xref:System.Threading.Tasks.ParallelOptions>, <xref:System.Threading.Tasks.ParallelLoopResult>, <xref:System.Threading.CancellationToken>a <xref:System.Threading.CancellationTokenSource>.  
  
 Další informace najdete v tématu [vzory pro paralelní programování: porozumění a použití paralelních vzorů s .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222).  
  
 PLINQ podporuje datový paralelismus s deklarativní syntaxí nebo dotazem, jako je syntaxe. Další informace naleznete v tématu [PARALLEL LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Zápis jednoduché smyčky Parallel.For](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|Popisuje, jak napsat smyčku <xref:System.Threading.Tasks.Parallel.For%2A> pro jakékoliv pole nebo indexovanou <xref:System.Collections.Generic.IEnumerable%601> kolekci zdroje.|  
|[Postupy: Zápis jednoduché smyčky Parallel.ForEach](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|Popisuje, jak napsat smyčku <xref:System.Threading.Tasks.Parallel.ForEach%2A> v jakékoli <xref:System.Collections.Generic.IEnumerable%601> zdrojové kolekci.|  
|[Postupy: zastavení nebo přerušení ze smyčky Parallel. for](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100))|Popisuje, jak zastavit nebo přerušit paralelní smyčka, aby všechna vlákna byla informována o akci.|  
|[Postupy: Zápis smyčky Parallel.For pomocí proměnných v místním vláknu](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Popisuje, jak napsat smyčku <xref:System.Threading.Tasks.Parallel.For%2A>, ve které každé vlákno udržuje soukromou proměnnou, která není viditelná pro žádné další podprocesy, a jak synchronizovat výsledky ze všech vláken po dokončení smyčky.|  
|[Postupy: Zápis smyčky Parallel.ForEach pomocí proměnných v místním oddílu](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)|Popisuje, jak napsat smyčku <xref:System.Threading.Tasks.Parallel.ForEach%2A>, ve které každé vlákno udržuje soukromou proměnnou, která není viditelná pro žádné další podprocesy, a jak synchronizovat výsledky ze všech vláken po dokončení smyčky.|  
|[Postupy: Zrušení smyčky Parallel.For nebo ForEach](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|Popisuje, jak zrušit paralelní smyčku pomocí <xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Postupy: Zrychlení malých smyček](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|Popisuje jeden způsob, jak zrychlit provádění, když je tělo smyčky velmi malé.|  
|[Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Poskytuje přehled úlohy paralelní knihovny.|  
|[Paralelní programování](../../../docs/standard/parallel-programming/index.md)|Zavádí paralelní programování v .NET Framework.|  
  
## <a name="see-also"></a>Viz také:

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
