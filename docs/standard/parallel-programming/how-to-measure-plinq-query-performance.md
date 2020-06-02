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
ms.openlocfilehash: f240b2c275305aec5699eb42406e0689925490a8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288183"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="ba037-102">Postupy: Měření výkonu dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="ba037-102">How to: Measure PLINQ Query Performance</span></span>

<span data-ttu-id="ba037-103">Tento příklad ukazuje, jak použít <xref:System.Diagnostics.Stopwatch> třídu k měření času, který je potřeba pro spuštění dotazu PLINQ.</span><span class="sxs-lookup"><span data-stu-id="ba037-103">This example shows how to use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba037-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba037-104">Example</span></span>  
 <span data-ttu-id="ba037-105">V tomto příkladu je použita prázdná `foreach` smyčka ( `For Each` v Visual Basic) pro měření doby potřebné k provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="ba037-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="ba037-106">Ve skutečném kódu smyčka obvykle obsahuje další kroky zpracování, které se přidávají do celkové doby provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="ba037-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="ba037-107">Všimněte si, že Stopwatch není spuštěný, dokud není těsně před smyčkou, protože to je po zahájení provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="ba037-107">Notice that the stopwatch is not started until just before the loop, because that's when the query execution begins.</span></span> <span data-ttu-id="ba037-108">Pokud potřebujete přesnější měření, můžete `ElapsedTicks` místo toho použít vlastnost `ElapsedMilliseconds` .</span><span class="sxs-lookup"><span data-stu-id="ba037-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="ba037-109">Celková doba spuštění je užitečnou metrikou při experimentování s implementacemi dotazů, ale nikdy neříká celému článku.</span><span class="sxs-lookup"><span data-stu-id="ba037-109">The total execution time is a useful metric when you are experimenting with query implementations, but it doesn't always tell the whole story.</span></span> <span data-ttu-id="ba037-110">Chcete-li získat hlubší a širší pohled na interakci s vlákny dotazů mezi sebou a s jinými běžícími procesy, použijte [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="ba037-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba037-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba037-111">See also</span></span>

- [<span data-ttu-id="ba037-112">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="ba037-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
