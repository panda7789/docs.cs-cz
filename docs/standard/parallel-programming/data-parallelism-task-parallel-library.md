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
ms.openlocfilehash: f414e5b0463e28427c8c60e2f8b8774ad6973da2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43464134"
---
# <a name="data-parallelism-task-parallel-library"></a>Datový paralelismus (Task Parallel Library)
*Datový paralelismus* odkazuje na scénáře, ve kterých se současně provádí stejnou operaci (paralelně) na prvky ve zdrojové kolekci nebo pole. V paralelní operace s daty zdrojové kolekce rozdělena tak, aby více vláken může souběžně pracovat na různých segmentů.  
  
 Task Parallel Library (TPL) podporuje datový paralelismus prostřednictvím <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> třídy. Tato třída poskytuje založených na volání metody paralelní implementace [pro](~/docs/csharp/language-reference/keywords/for.md) a [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) smyčky (`For` a `For Each` v jazyce Visual Basic). Zápis logiky smyčky pro <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> smyčky podobně jako sekvenční smyčka. Není nutné k vytvoření vlákna nebo fronty pracovních položek. V základní smyčky není třeba provádět zámky. Knihovna TPL zpracovává nízké úrovně práci za vás. Podrobné informace o použití <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, stáhněte si dokument [vzory paralelního programování: Principy a používání paralelních vzorů s rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222). Následující příklad kódu ukazuje jednoduchý `foreach` smyčky a paralelní ekvivalentní.  
  
> [!NOTE]
>  Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Když je paralelní smyčka spuštěna, oddíly TPL zdroj dat tak, aby smyčky může pracovat souběžně na více částí. Plánovač úloh na pozadí oddíly úkolů na základě systémových prostředků a úloh. Pokud je to možné, Plánovač přerozděluje práci mezi více vláken a procesory, pokud nevyvážené zatížení.  
  
> [!NOTE]
>  Můžete také zadat vlastní vlastního rozdělovače nebo plánovač. Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) a [Plánovačích úkolů](https://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65).  
  
 Jak <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody mají několik přetížení, které umožňují můžete zastavit nebo přerušit provádění smyčky, sledovat stav smyčky v jiných vláknech, zachovat stav místního vlákna, dokončení místních objektů, řídit stupeň souběžnosti, a tak dále. Typy pomocné rutiny, které tuto funkci povolit, zahrnují <xref:System.Threading.Tasks.ParallelLoopState>, <xref:System.Threading.Tasks.ParallelOptions>, <xref:System.Threading.Tasks.ParallelLoopResult>, <xref:System.Threading.CancellationToken>, a <xref:System.Threading.CancellationTokenSource>.  
  
 Další informace najdete v tématu [vzory paralelního programování: Principy a používání paralelních vzorů s rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222).  
  
 Datový paralelismus syntaxí deklarativní, nebo jako dotaz, PLINQ podporuje. Další informace najdete v tématu [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Zápis jednoduché smyčky Parallel.For](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|Popisuje, jak psát <xref:System.Threading.Tasks.Parallel.For%2A> smyčky přes jakékoli pole nebo indexovanou <xref:System.Collections.Generic.IEnumerable%601> zdrojové kolekce.|  
|[Postupy: Zápis jednoduché smyčky Parallel.ForEach](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|Popisuje, jak psát <xref:System.Threading.Tasks.Parallel.ForEach%2A> žádné ve smyčce <xref:System.Collections.Generic.IEnumerable%601> zdrojové kolekce.|  
|[Postupy: zastavení nebo přerušení smyčky Parallel.For](https://msdn.microsoft.com/library/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e)|Popisuje způsob zastavení nebo přerušení paralelní smyčky tak, aby všechna vlákna budou informováni akce.|  
|[Postupy: Zápis smyčky Parallel.For pomocí proměnných v místním vláknu](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Popisuje, jak psát <xref:System.Threading.Tasks.Parallel.For%2A> smyčku, ve kterém každý podproces udržuje privátní proměnnou, která není viditelné pro ostatní vlákna a synchronizace výsledků ze všech vláken, po dokončení smyčky.|  
|[Postupy: Zápis smyčky Parallel.ForEach pomocí proměnných v místním oddílu](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)|Popisuje, jak psát <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčku, ve kterém každý podproces udržuje privátní proměnnou, která není viditelné pro ostatní vlákna a synchronizace výsledků ze všech vláken, po dokončení smyčky.|  
|[Postupy: Zrušení smyčky Parallel.For nebo ForEach](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|Popisuje, jak zrušit paralelní smyčky pomocí <xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Postupy: Zrychlení malých smyček](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|Popisuje jeden ze způsobů pro urychlení spuštění, pokud tělo smyčky je velmi malý.|  
|[Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Poskytuje přehled o Task Parallel Library.|  
|[Paralelní programování](../../../docs/standard/parallel-programming/index.md)|Zavádí paralelní programování v rozhraní .NET Framework.|  
  
## <a name="see-also"></a>Viz také  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
