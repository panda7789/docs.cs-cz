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
ms.openlocfilehash: d29137127dd47844f8f08d3ac689cf2827d9efe2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288222"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="62c14-102">Postupy: Zrušení smyček Parallel.For nebo ForEach</span><span class="sxs-lookup"><span data-stu-id="62c14-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="62c14-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>Metody a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> podporují zrušení pomocí tokenů zrušení.</span><span class="sxs-lookup"><span data-stu-id="62c14-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="62c14-104">Další informace o zrušení obecně naleznete v tématu [zrušení](../threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="62c14-104">For more information about cancellation in general, see [Cancellation](../threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="62c14-105">V paralelní smyčce můžete zadat <xref:System.Threading.CancellationToken> metodu do <xref:System.Threading.Tasks.ParallelOptions> parametru a potom uzavřít paralelní volání do bloku try-catch.</span><span class="sxs-lookup"><span data-stu-id="62c14-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62c14-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="62c14-106">Example</span></span>  
 <span data-ttu-id="62c14-107">Následující příklad ukazuje, jak zrušit volání <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="62c14-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="62c14-108">Můžete použít stejný přístup ke <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> volání.</span><span class="sxs-lookup"><span data-stu-id="62c14-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="62c14-109">Pokud token, který signalizuje zrušení, je stejný token, který je určen v <xref:System.Threading.Tasks.ParallelOptions> instanci, pak paralelní smyčka vyvolá jednu <xref:System.OperationCanceledException> při zrušení.</span><span class="sxs-lookup"><span data-stu-id="62c14-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="62c14-110">Pokud nějaký jiný token způsobí zrušení, smyčka vyvolá výjimku <xref:System.AggregateException> s <xref:System.OperationCanceledException> jako InnerException.</span><span class="sxs-lookup"><span data-stu-id="62c14-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62c14-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="62c14-111">See also</span></span>

- [<span data-ttu-id="62c14-112">Datový paralelismus</span><span class="sxs-lookup"><span data-stu-id="62c14-112">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="62c14-113">Výrazy lambda v PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="62c14-113">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
