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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139746"
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="18d18-102">Postupy: Zrychlení malých smyček</span><span class="sxs-lookup"><span data-stu-id="18d18-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="18d18-103">Pokud má <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> smyčka malý text, může to být pomalejší než ekvivalentní sekvenční smyčka, jako je například smyčka [for](../../csharp/language-reference/keywords/for.md) v C# a smyčka [for](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="18d18-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](../../csharp/language-reference/keywords/for.md) loop in C# and the [For](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) loop in Visual Basic.</span></span> <span data-ttu-id="18d18-104">Pomalejší výkon je způsoben režijními náklady souvisejícími s rozdělením dat do oddílů a náklady na vyvolání delegáta v každé iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="18d18-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="18d18-105">Pro řešení takových scénářů poskytuje třída <xref:System.Collections.Concurrent.Partitioner> <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metodu, která umožňuje poskytnout sekvenční smyčku pro tělo delegáta, aby byl delegát vyvolán pouze jednou pro každý oddíl, nikoli jednou pro iteraci.</span><span class="sxs-lookup"><span data-stu-id="18d18-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="18d18-106">Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="18d18-106">For more information, see [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="18d18-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="18d18-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="18d18-108">Přístup, který ukazuje tento příklad, je užitečný, když smyčka provede minimální množství práce.</span><span class="sxs-lookup"><span data-stu-id="18d18-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="18d18-109">Jakmile se práce vyřadí efektivněji, budete pravděpodobně mít stejný nebo lepší výkon pomocí <xref:System.Threading.Tasks.Parallel.For%2A> nebo <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky s výchozím rozdělovačem.</span><span class="sxs-lookup"><span data-stu-id="18d18-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18d18-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18d18-110">See also</span></span>

- [<span data-ttu-id="18d18-111">Datový paralelismus</span><span class="sxs-lookup"><span data-stu-id="18d18-111">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="18d18-112">Vlastní dělicí metody pro PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="18d18-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [<span data-ttu-id="18d18-113">Iterátory (C#)</span><span class="sxs-lookup"><span data-stu-id="18d18-113">Iterators (C#)</span></span>](../../csharp/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="18d18-114">Iterátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18d18-114">Iterators (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="18d18-115">Výrazy lambda v PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="18d18-115">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
