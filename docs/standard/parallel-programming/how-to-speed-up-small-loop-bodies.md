---
title: 'Postupy: Zrychlení malých smyček'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fde68d0a938ed04380bf0e99cc0c544793571d77
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965576"
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="83c15-102">Postupy: Zrychlení malých smyček</span><span class="sxs-lookup"><span data-stu-id="83c15-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="83c15-103">Když <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> má malé tělo smyčky, jako například může pomaleji než ekvivalentní sekvenčních smyčkách, proveďte [pro](../../csharp/language-reference/keywords/for.md) smyčky v C# a [pro](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) smyčky v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="83c15-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](../../csharp/language-reference/keywords/for.md) loop in C# and the [For](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) loop in Visual Basic.</span></span> <span data-ttu-id="83c15-104">Snížení výkonu způsobuje režie spojená s dělení dat a náklady na volání delegáta při každé iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="83c15-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="83c15-105">K řešení scénářů, <xref:System.Collections.Concurrent.Partitioner> třída poskytuje <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metodu, která umožňuje poskytovat sekvenčních smyčkách pro tělo delegáta, tak, aby je delegát vyvolán jenom jednou na oddíl, ne jednou za iteraci.</span><span class="sxs-lookup"><span data-stu-id="83c15-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="83c15-106">Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="83c15-106">For more information, see [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="83c15-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="83c15-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="83c15-108">Přístup předvedené v tomto příkladu je užitečný, pokud smyčka provádí minimální množství práce.</span><span class="sxs-lookup"><span data-stu-id="83c15-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="83c15-109">Jakmile je výpočetně náročná, bude pravděpodobně získat stejný nebo lepší výkon pomocí <xref:System.Threading.Tasks.Parallel.For%2A> nebo <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky pomocí výchozího rozdělovače.</span><span class="sxs-lookup"><span data-stu-id="83c15-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83c15-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83c15-110">See also</span></span>

- [<span data-ttu-id="83c15-111">Datový paralelismus</span><span class="sxs-lookup"><span data-stu-id="83c15-111">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="83c15-112">Vlastní dělicí metody pro PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="83c15-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [<span data-ttu-id="83c15-113">Iterátory (C#)</span><span class="sxs-lookup"><span data-stu-id="83c15-113">Iterators (C#)</span></span>](../../csharp/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="83c15-114">Iterátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83c15-114">Iterators (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="83c15-115">Výrazy lambda v PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="83c15-115">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
