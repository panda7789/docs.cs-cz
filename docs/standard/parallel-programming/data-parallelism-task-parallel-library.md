---
title: "Datový paralelismus (Task Parallel Library)"
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
helpviewer_keywords: parallelism, data
ms.assetid: 3f05f33f-f1da-4b16-81c2-9ceff1bef449
caps.latest.revision: "25"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7fa35e58ed142e6a957326893613ac465e668c45
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="data-parallelism-task-parallel-library"></a>Datový paralelismus (Task Parallel Library)
*Datový paralelismus* popisuje scénáře, ve kterých stejné operace se provádí současně (paralelně) u elementů ve zdrojové kolekci nebo pole. Zdrojové kolekci je v paralelních operací dat, na oddíly tak, aby více vláken může fungovat v různých segmentech současně.  
  
 Datový paralelismus prostřednictvím podporuje Task Parallel Library (TPL) <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> třídy. Tato třída poskytuje na základě metod paralelní implementace [pro](~/docs/csharp/language-reference/keywords/for.md) a [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) smyčky (`For` a `For Each` v jazyce Visual Basic). Zápis smyčky logiku pro <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> obdobný jako sekvenční smyčky. Nemáte k vytvoření vlákna nebo pracovních položek ve frontě. V základní smyčky není třeba provádět zámky. TPL zpracovává všechny pracovní nízké úrovně pro vás. Podrobné informace o použití <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, stáhněte si dokument [vzory pro paralelní programování: pochopení a použití Parallel Patterns pomocí rozhraní .NET Framework 4](http://www.microsoft.com/download/details.aspx?id=19222). Následující příklad kódu ukazuje jednoduchý `foreach` smyčky a paralelní ekvivalentní.  
  
> [!NOTE]
>  Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s výrazy lambda v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Když je paralelní smyčka spuštěna, oddíly TPL zdroj dat tak, aby smyčky můžete pracovat s více částmi souběžně. Plánovač úloh na pozadí oddíly úkolů na základě systémové prostředky a zatížení. Pokud je to možné, Plánovač úloh přestane být nevyváženou znovu distribuuje pracovní mezi více vláken a procesory.  
  
> [!NOTE]
>  Můžete také zadat vlastní vlastní dělicí metody nebo plánovače. Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) a [plánovače úloh](http://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65).  
  
 Jak <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody mají několik přetížení, která umožňují můžete zastavit nebo přerušení provádění smyčky, sledovat stav smyčky na jiná vlákna, udržovat místní stav, finalizovat místní objekty, řídit stupeň souběžnosti, a tak dále. Typy pomocné rutiny, které tuto funkci povolit, zahrnují <xref:System.Threading.Tasks.ParallelLoopState>, <xref:System.Threading.Tasks.ParallelOptions>, <xref:System.Threading.Tasks.ParallelLoopResult>, <xref:System.Threading.CancellationToken>, a <xref:System.Threading.CancellationTokenSource>.  
  
 Další informace najdete v tématu [vzory z paralelní programování](http://go.microsoft.com/fwlink/p/?LinkId=265491).  
  
 Datový paralelismus s deklarativní nebo dotazu jako syntaxe je podporován PLINQ. Další informace najdete v tématu [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Zápis jednoduché smyčky Parallel.For](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|Popisuje, jak napsat <xref:System.Threading.Tasks.Parallel.For%2A> smyčky přes žádné pole nebo indexovanou <xref:System.Collections.Generic.IEnumerable%601> zdroje kolekce.|  
|[Postupy: Zápis jednoduché smyčky Parallel.ForEach](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|Popisuje, jak napsat <xref:System.Threading.Tasks.Parallel.ForEach%2A> žádné opakovací smyčku <xref:System.Collections.Generic.IEnumerable%601> zdroje kolekce.|  
|[Postupy: zastavení nebo přerušení smyčky Parallel.For](http://msdn.microsoft.com/en-us/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e)|Popisuje, jak pro zastavení nebo přerušení paralelní smyčky tak, aby všechna vlákna informovány o akci.|  
|[Postupy: Zápis smyčky Parallel.For pomocí proměnných v místním vláknu](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Popisuje, jak napsat <xref:System.Threading.Tasks.Parallel.For%2A> smyčky, ve kterém každé vlákno udržuje soukromé proměnné, která není viditelná pro žádné další podprocesy a jak synchronizovat výsledky ze všech vláken po dokončení smyčky.|  
|[Postupy: Zápis smyčky Parallel.ForEach pomocí proměnných v místním vláknu](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md)|Popisuje, jak napsat <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky, ve kterém každé vlákno udržuje soukromé proměnné, která není viditelná pro žádné další podprocesy a jak synchronizovat výsledky ze všech vláken po dokončení smyčky.|  
|[Postupy: Zrušení smyčky Parallel.For nebo ForEach](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|Popisuje, jak zrušit paralelní smyčky pomocí<xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Postupy: Zrychlení malých smyček](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|Popisuje jeden způsob, jak urychlit spuštění těla smyčky jsou velmi malé.|  
|[Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Poskytuje přehled Task Parallel Library.|  
|[Paralelní programování](../../../docs/standard/parallel-programming/index.md)|Představuje paralelní programování v rozhraní .NET Framework.|  
  
## <a name="see-also"></a>Viz také  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
