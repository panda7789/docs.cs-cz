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
ms.openlocfilehash: 4983cafb9d4a72262dc7a6a6c37fab23937b3274
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288079"
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="6cd0f-102">Postupy: Zrychlení malých smyček</span><span class="sxs-lookup"><span data-stu-id="6cd0f-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="6cd0f-103">Pokud <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> má smyčka malý text, může to být pomalejší než ekvivalentní sekvenční smyčka, jako je například smyčka [for](../../csharp/language-reference/keywords/for.md) v jazyce C# a smyčka [for](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6cd0f-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](../../csharp/language-reference/keywords/for.md) loop in C# and the [For](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) loop in Visual Basic.</span></span> <span data-ttu-id="6cd0f-104">Pomalejší výkon je způsoben režijními náklady souvisejícími s rozdělením dat do oddílů a náklady na vyvolání delegáta v každé iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="6cd0f-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="6cd0f-105">Pro řešení takových scénářů <xref:System.Collections.Concurrent.Partitioner> Třída poskytuje <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metodu, která umožňuje poskytnout sekvenční smyčku pro tělo delegáta, aby byl delegát vyvolán pouze jednou pro každý oddíl, nikoli jednou pro iteraci.</span><span class="sxs-lookup"><span data-stu-id="6cd0f-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="6cd0f-106">Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="6cd0f-106">For more information, see [Custom Partitioners for PLINQ and TPL](custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cd0f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="6cd0f-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="6cd0f-108">Přístup, který ukazuje tento příklad, je užitečný, když smyčka provede minimální množství práce.</span><span class="sxs-lookup"><span data-stu-id="6cd0f-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="6cd0f-109">Jakmile se práce vyřadí efektivněji, budete pravděpodobně mít stejný nebo lepší výkon pomocí <xref:System.Threading.Tasks.Parallel.For%2A> <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky nebo s výchozím rozdělovačem.</span><span class="sxs-lookup"><span data-stu-id="6cd0f-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd0f-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="6cd0f-110">See also</span></span>

- [<span data-ttu-id="6cd0f-111">Datový paralelismus</span><span class="sxs-lookup"><span data-stu-id="6cd0f-111">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="6cd0f-112">Vlastní dělicí metody pro PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="6cd0f-112">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
- [<span data-ttu-id="6cd0f-113">Iterátory (C#)</span><span class="sxs-lookup"><span data-stu-id="6cd0f-113">Iterators (C#)</span></span>](../../csharp/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="6cd0f-114">Iterátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6cd0f-114">Iterators (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="6cd0f-115">Výrazy lambda v PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="6cd0f-115">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
