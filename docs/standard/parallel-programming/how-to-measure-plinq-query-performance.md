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
ms.openlocfilehash: 91b6165be2f4f464626fb25f7152de68de9d86e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124997"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="f9fe8-102">Postupy: Měření výkonu dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="f9fe8-102">How to: Measure PLINQ Query Performance</span></span>
<span data-ttu-id="f9fe8-103">Tento příklad ukazuje, jak použít třídu <xref:System.Diagnostics.Stopwatch> k měření doby potřebné k provedení dotazu PLINQ.</span><span class="sxs-lookup"><span data-stu-id="f9fe8-103">This example shows how use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9fe8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9fe8-104">Example</span></span>  
 <span data-ttu-id="f9fe8-105">V tomto příkladu je použita prázdná smyčka `foreach` (`For Each` v Visual Basic) pro měření doby potřebné k provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="f9fe8-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="f9fe8-106">Ve skutečném kódu smyčka obvykle obsahuje další kroky zpracování, které se přidávají do celkové doby provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="f9fe8-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="f9fe8-107">Všimněte si, že Stopwatch není spuštěn, dokud není těsně před smyčkou, protože to je, když je zahájeno provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="f9fe8-107">Notice that the stopwatch is not started until just before the loop, because that is when the query execution begins.</span></span> <span data-ttu-id="f9fe8-108">Pokud potřebujete přesnější měření, můžete místo `ElapsedMilliseconds`použít vlastnost `ElapsedTicks`.</span><span class="sxs-lookup"><span data-stu-id="f9fe8-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="f9fe8-109">Celková doba spuštění je užitečnou metrikou při experimentování s implementacemi dotazů, ale nikdy neříká celému článku.</span><span class="sxs-lookup"><span data-stu-id="f9fe8-109">The total execution time is a useful metric when you are experimenting with query implementations, but it does not always tell the whole story.</span></span> <span data-ttu-id="f9fe8-110">Chcete-li získat hlubší a širší pohled na interakci s vlákny dotazů mezi sebou a s jinými běžícími procesy, použijte Vizualizátor souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="f9fe8-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the Concurrency Visualizer.</span></span> <span data-ttu-id="f9fe8-111">Další informace najdete v tématu [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="f9fe8-111">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9fe8-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9fe8-112">See also</span></span>

- [<span data-ttu-id="f9fe8-113">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="f9fe8-113">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
