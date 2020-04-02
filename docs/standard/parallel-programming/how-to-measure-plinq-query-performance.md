---
title: 'Postupy: Měření výkonu dotazu PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: 4cb0d408798d66c8491654c90f33255c700690a3
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587785"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="ae19e-102">Postupy: Měření výkonu dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="ae19e-102">How to: Measure PLINQ Query Performance</span></span>
<span data-ttu-id="ae19e-103">Tento příklad ukazuje, <xref:System.Diagnostics.Stopwatch> jak použít třídu k měření času, který trvá pro dotaz PLINQ spustit.</span><span class="sxs-lookup"><span data-stu-id="ae19e-103">This example shows how use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae19e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae19e-104">Example</span></span>  
 <span data-ttu-id="ae19e-105">Tento příklad používá `foreach` prázdnou smyčku (`For Each` v jazyce Visual Basic) k měření doby, která trvá spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="ae19e-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="ae19e-106">V kódu reálného světa smyčky obvykle obsahuje další kroky zpracování, které přidávají k celkové době spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="ae19e-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="ae19e-107">Všimněte si, že stopky není spuštěna až těsně před smyčky, protože to je při spuštění dotazu začíná.</span><span class="sxs-lookup"><span data-stu-id="ae19e-107">Notice that the stopwatch is not started until just before the loop, because that is when the query execution begins.</span></span> <span data-ttu-id="ae19e-108">Pokud požadujete více jemně odstupňovaného `ElapsedTicks` měření, `ElapsedMilliseconds`můžete použít vlastnost namísto .</span><span class="sxs-lookup"><span data-stu-id="ae19e-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="ae19e-109">Celková doba provádění je užitečná metrika při experimentování s implementacemi dotazu, ale ne vždy vypovídá celý příběh.</span><span class="sxs-lookup"><span data-stu-id="ae19e-109">The total execution time is a useful metric when you are experimenting with query implementations, but it does not always tell the whole story.</span></span> <span data-ttu-id="ae19e-110">Chcete-li získat hlubší a bohatší zobrazení interakce vláken dotazu mezi sebou a s jinými spuštěnými procesy, použijte vizualizér souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="ae19e-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the Concurrency Visualizer.</span></span> <span data-ttu-id="ae19e-111">Další informace naleznete v tématu [Vizualizér souběžnosti](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="ae19e-111">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae19e-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae19e-112">See also</span></span>

- [<span data-ttu-id="ae19e-113">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="ae19e-113">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
