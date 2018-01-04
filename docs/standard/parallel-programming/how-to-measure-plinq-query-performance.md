---
title: "Postupy: Měření výkonu dotazu PLINQ"
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
helpviewer_keywords: PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fe19fd6ae7730a30a9ccc8a39b99a31981f838fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="b5efc-102">Postupy: Měření výkonu dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="b5efc-102">How to: Measure PLINQ Query Performance</span></span>
<span data-ttu-id="b5efc-103">Tento příklad ukazuje, jak používat <xref:System.Diagnostics.Stopwatch> třída k měření doby potřebné pro PLINQ dotazu provést.</span><span class="sxs-lookup"><span data-stu-id="b5efc-103">This example shows how use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5efc-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5efc-104">Example</span></span>  
 <span data-ttu-id="b5efc-105">Tento příklad používá prázdnou `foreach` smyčky (`For Each` v jazyce Visual Basic) k měření doby potřebné k provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="b5efc-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="b5efc-106">V kódu reálného smyčky obvykle obsahuje další zpracování kroky, které přidat do doba provádění dotazu na celkový počet.</span><span class="sxs-lookup"><span data-stu-id="b5efc-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="b5efc-107">Všimněte si, že stopky není spustit, dokud nebude jen před smyčky, protože se jedná, kdy se zahájí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="b5efc-107">Notice that the stopwatch is not started until just before the loop, because that is when the query execution begins.</span></span> <span data-ttu-id="b5efc-108">Pokud budete potřebovat další podrobných měření, můžete použít `ElapsedTicks` vlastnost místo `ElapsedMilliseconds`.</span><span class="sxs-lookup"><span data-stu-id="b5efc-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="b5efc-109">Celková doba provádění je užitečné metriky, když testujete implementace dotazu, ale jeho není vždy všechno.</span><span class="sxs-lookup"><span data-stu-id="b5efc-109">The total execution time is a useful metric when you are experimenting with query implementations, but it does not always tell the whole story.</span></span> <span data-ttu-id="b5efc-110">Chcete-li získat podrobnější a bohatší zobrazení interakce vláken dotazu sebou a s jinými spuštěné procesy, použijte vizualizér souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="b5efc-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the Concurrency Visualizer.</span></span> <span data-ttu-id="b5efc-111">Další informace najdete v tématu [vizualizér souběžnosti](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="b5efc-111">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5efc-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5efc-112">See Also</span></span>  
 [<span data-ttu-id="b5efc-113">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="b5efc-113">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
