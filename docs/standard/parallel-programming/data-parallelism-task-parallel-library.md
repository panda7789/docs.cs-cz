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
ms.openlocfilehash: d7500666f12624d1a81d399a325827a416e5af3c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276774"
---
# <a name="data-parallelism-task-parallel-library"></a>Datový paralelismus (Task Parallel Library)
*Datový paralelismus* odkazuje na scénáře, ve kterých je stejná operace provedena souběžně (paralelně) na prvcích ve zdrojové kolekci nebo poli. V datech paralelních operacích je zdrojová kolekce rozdělená tak, aby více vláken mohlo současně pracovat s různými segmenty.  
  
 Task Parallel Library (TPL) podporuje datový paralelismuing prostřednictvím <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> třídy. Tato třída poskytuje paralelní implementace smyček [pro](../../csharp/language-reference/keywords/for.md) a [foreach](../../csharp/language-reference/keywords/foreach-in.md) ( `For` a `For Each` v Visual Basic) založené na metodách. Logiku smyčky můžete napsat pro <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> smyčku nebo, která <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> je velká, protože byste napsali sekvenční smyčku. Nemusíte vytvářet vlákna nebo pracovní položky zařazené do fronty. V základních smyčkách nemusíte přijímat zámky. TPL zpracovává veškerou práci na nízké úrovni za vás. Pro podrobné informace o použití <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> Stáhněte si [vzory dokumentů pro paralelní programování: porozumění a použití paralelních vzorů s .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222). Následující příklad kódu ukazuje jednoduchou `foreach` smyčku a její paralelní ekvivalent.  
  
> [!NOTE]
> Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Při spuštění paralelní smyčky aplikace TPL rozdělí zdroj dat tak, aby smyčka mohla pracovat na více částech současně. Na pozadí Plánovač úloh rozdělí úkol na základě systémových prostředků a zatížení. Pokud je to možné, Scheduler rozšíří práci mezi několika vlákny a procesory, pokud dojde k nevyrovnanému zatížení.  
  
> [!NOTE]
> Můžete také dodat vlastní rozdělovač nebo Plánovač. Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](custom-partitioners-for-plinq-and-tpl.md) a [plánovače úloh](xref:System.Threading.Tasks.TaskScheduler).  
  
 Obě <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> mají několik přetížení, která umožňují zastavit nebo přerušit provádění smyčky, monitorovat stav smyčky v jiných vláknech, udržovat místní stav vlákna, finalizovat místní objekty vlákna, řídit stupeň souběžnosti a tak dále. Pomocné typy, které umožňují tuto funkci, zahrnují <xref:System.Threading.Tasks.ParallelLoopState> , <xref:System.Threading.Tasks.ParallelOptions> ,, <xref:System.Threading.Tasks.ParallelLoopResult> <xref:System.Threading.CancellationToken> a <xref:System.Threading.CancellationTokenSource> .  
  
 Další informace najdete v tématu [vzory pro paralelní programování: porozumění a použití paralelních vzorů s .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222).  
  
 PLINQ podporuje datový paralelismus s deklarativní syntaxí nebo dotazem, jako je syntaxe. Další informace naleznete v tématu [PARALLEL LINQ (PLINQ)](introduction-to-plinq.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Postupy: Zápis jednoduché smyčky Parallel.For](how-to-write-a-simple-parallel-for-loop.md)|Popisuje, jak napsat <xref:System.Threading.Tasks.Parallel.For%2A> smyčku přes jakékoli pole nebo indexovanou <xref:System.Collections.Generic.IEnumerable%601> zdrojovou kolekci.|  
|[Postupy: Zápis jednoduché smyčky Parallel.ForEach](how-to-write-a-simple-parallel-foreach-loop.md)|Popisuje, jak napsat <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčku přes jakoukoli <xref:System.Collections.Generic.IEnumerable%601> zdrojovou kolekci.|  
|[Postupy: zastavení nebo přerušení ze smyčky Parallel. for](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100))|Popisuje, jak zastavit nebo přerušit paralelní smyčka, aby všechna vlákna byla informována o akci.|  
|[Postupy: Zápis smyčky Parallel.For pomocí proměnných v místním vláknu](how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Popisuje, jak napsat <xref:System.Threading.Tasks.Parallel.For%2A> smyčku, ve které každé vlákno udržuje soukromou proměnnou, která není viditelná pro žádné další podprocesy, a jak synchronizovat výsledky ze všech vláken po dokončení smyčky.|  
|[Postupy: Zápis smyčky Parallel.ForEach pomocí proměnných v místním oddílu](how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)|Popisuje, jak napsat <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčku, ve které každé vlákno udržuje soukromou proměnnou, která není viditelná pro žádné další podprocesy, a jak synchronizovat výsledky ze všech vláken po dokončení smyčky.|  
|[Postupy: Zrušení smyček Parallel.For nebo ForEach](how-to-cancel-a-parallel-for-or-foreach-loop.md)|Popisuje, jak zrušit paralelní smyčku pomocí<xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Postupy: Zrychlení malých smyček](how-to-speed-up-small-loop-bodies.md)|Popisuje jeden způsob, jak zrychlit provádění, když je tělo smyčky velmi malé.|  
|[Task Parallel Library (TPL)](task-parallel-library-tpl.md)|Poskytuje přehled úlohy paralelní knihovny.|  
|[Paralelní programování](index.md)|Zavádí paralelní programování v .NET Framework.|  
  
## <a name="see-also"></a>Viz také

- [Paralelní programování](index.md)
