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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd9e3a0ead62450e87225212f4fc6ecec6ec9489
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45533461"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="f7554-102">Postupy: Měření výkonu dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="f7554-102">How to: Measure PLINQ Query Performance</span></span>
<span data-ttu-id="f7554-103">Tento příklad ukazuje způsob použití <xref:System.Diagnostics.Stopwatch> třídy k měření čas potřebný k provedení PLINQ dotazu.</span><span class="sxs-lookup"><span data-stu-id="f7554-103">This example shows how use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7554-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7554-104">Example</span></span>  
 <span data-ttu-id="f7554-105">V tomto příkladu prázdný `foreach` smyčky (`For Each` v jazyce Visual Basic) k měření čas potřebný pro dotaz můžete spustit.</span><span class="sxs-lookup"><span data-stu-id="f7554-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="f7554-106">V reálné kód smyčky obvykle obsahuje další kroky, které aplikacím dodávají doba provádění dotazu na celkový počet.</span><span class="sxs-lookup"><span data-stu-id="f7554-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="f7554-107">Všimněte si, že je stopky spustit, až bude vždy před provedením smyčky, vzhledem k tomu, že začne provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="f7554-107">Notice that the stopwatch is not started until just before the loop, because that is when the query execution begins.</span></span> <span data-ttu-id="f7554-108">Pokud budete potřebovat další jemné měření, můžete použít `ElapsedTicks` vlastnosti namísto `ElapsedMilliseconds`.</span><span class="sxs-lookup"><span data-stu-id="f7554-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="f7554-109">Celkové doby provádění je užitečné metriky, když jsou experimentování s implementacemi dotazu, ale to není vždy poskytují kompletní představu.</span><span class="sxs-lookup"><span data-stu-id="f7554-109">The total execution time is a useful metric when you are experimenting with query implementations, but it does not always tell the whole story.</span></span> <span data-ttu-id="f7554-110">Chcete-li získat podrobnější a bohatší zobrazení interakce vláken dotazů mezi sebou a s ostatními spuštěné procesy, použijte Vizualizátor souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="f7554-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the Concurrency Visualizer.</span></span> <span data-ttu-id="f7554-111">Další informace najdete v tématu [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="f7554-111">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7554-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7554-112">See also</span></span>

- [<span data-ttu-id="f7554-113">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="f7554-113">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
