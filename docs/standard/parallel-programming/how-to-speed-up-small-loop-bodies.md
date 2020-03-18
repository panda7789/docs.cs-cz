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
ms.openlocfilehash: 29d7fa8200ddd972c1a5c98ea6f30a7c8ff732e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139746"
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="9f746-102">Postupy: Zrychlení malých smyček</span><span class="sxs-lookup"><span data-stu-id="9f746-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="9f746-103">Pokud <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> má smyčka malé tělo, může provádět pomaleji než ekvivalentní sekvenční smyčka, jako je například [smyčka for](../../csharp/language-reference/keywords/for.md) v jazyce C# a [smyčka For](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9f746-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](../../csharp/language-reference/keywords/for.md) loop in C# and the [For](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) loop in Visual Basic.</span></span> <span data-ttu-id="9f746-104">Pomalejší výkon je způsoben režií, která se podílí na dělení dat, a náklady na vyvolání delegáta v každé iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="9f746-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="9f746-105">Chcete-li řešit <xref:System.Collections.Concurrent.Partitioner> tyto scénáře, třída poskytuje metodu, <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> která umožňuje poskytnout sekvenční smyčky pro tělo delegáta, tak, aby delegát je vyvolána pouze jednou za oddíl, namísto jednou za iteraci.</span><span class="sxs-lookup"><span data-stu-id="9f746-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="9f746-106">Další informace naleznete [v tématu Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="9f746-106">For more information, see [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f746-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f746-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="9f746-108">Přístup demonstrovaný v tomto příkladu je užitečný, když smyčka provádí minimální množství práce.</span><span class="sxs-lookup"><span data-stu-id="9f746-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="9f746-109">Vzhledem k tomu, že práce se stává více výpočetní nákladné, <xref:System.Threading.Tasks.Parallel.For%2A> budete <xref:System.Threading.Tasks.Parallel.ForEach%2A> pravděpodobně získat stejný nebo lepší výkon pomocí nebo smyčky s výchozím partitioner.</span><span class="sxs-lookup"><span data-stu-id="9f746-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f746-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f746-110">See also</span></span>

- [<span data-ttu-id="9f746-111">Datový paralelismus</span><span class="sxs-lookup"><span data-stu-id="9f746-111">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="9f746-112">Vlastní dělicí metody pro PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="9f746-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [<span data-ttu-id="9f746-113">Iterátory (C#)</span><span class="sxs-lookup"><span data-stu-id="9f746-113">Iterators (C#)</span></span>](../../csharp/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="9f746-114">Iterátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f746-114">Iterators (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="9f746-115">Výrazy lambda v PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="9f746-115">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
