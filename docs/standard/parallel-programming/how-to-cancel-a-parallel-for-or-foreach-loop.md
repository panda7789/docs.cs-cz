---
title: 'Postupy: Zrušení smyček Parallel.For nebo ForEach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
ms.openlocfilehash: 67f1f91f235cc88deaa97d412f368819ae0a8cda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134235"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="0a177-102">Postupy: Zrušení smyček Parallel.For nebo ForEach</span><span class="sxs-lookup"><span data-stu-id="0a177-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="0a177-103">Metody <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> a podporují zrušení pomocí tokenů zrušení.</span><span class="sxs-lookup"><span data-stu-id="0a177-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="0a177-104">Další informace o zrušení obecně naleznete v tématu [Zrušení](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="0a177-104">For more information about cancellation in general, see [Cancellation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="0a177-105">V paralelní smyčce zadáte <xref:System.Threading.CancellationToken> metodu v <xref:System.Threading.Tasks.ParallelOptions> parametru a pak uzavřete paralelní volání do bloku try-catch.</span><span class="sxs-lookup"><span data-stu-id="0a177-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a177-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a177-106">Example</span></span>  
 <span data-ttu-id="0a177-107">Následující příklad ukazuje, jak zrušit <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>volání do .</span><span class="sxs-lookup"><span data-stu-id="0a177-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0a177-108">Můžete použít stejný přístup <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> k volání.</span><span class="sxs-lookup"><span data-stu-id="0a177-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="0a177-109">Pokud token, který signalizuje zrušení je stejný <xref:System.Threading.Tasks.ParallelOptions> token, který je zadán v <xref:System.OperationCanceledException> instanci, pak paralelní smyčky vyvolá jeden na zrušení.</span><span class="sxs-lookup"><span data-stu-id="0a177-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="0a177-110">Pokud některé jiné token způsobí zrušení, <xref:System.AggregateException> smyčky <xref:System.OperationCanceledException> vyvolá s jako InnerException.</span><span class="sxs-lookup"><span data-stu-id="0a177-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a177-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a177-111">See also</span></span>

- [<span data-ttu-id="0a177-112">Datový paralelismus</span><span class="sxs-lookup"><span data-stu-id="0a177-112">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="0a177-113">Výrazy lambda v PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="0a177-113">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
