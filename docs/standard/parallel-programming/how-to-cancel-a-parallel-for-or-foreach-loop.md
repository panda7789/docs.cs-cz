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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce9b8b0864f3ed30c2ff03866abdb0d5d07991db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580387"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="7cb4e-102">Postupy: Zrušení smyček Parallel.For nebo ForEach</span><span class="sxs-lookup"><span data-stu-id="7cb4e-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="7cb4e-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody podporují zrušení prostřednictvím zrušení tokenů.</span><span class="sxs-lookup"><span data-stu-id="7cb4e-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="7cb4e-104">Další informace o zrušení obecně platí, najdete v části [zrušení](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="7cb4e-104">For more information about cancellation in general, see [Cancellation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="7cb4e-105">V paralelní smyčky, zadáte <xref:System.Threading.CancellationToken> metodu v <xref:System.Threading.Tasks.ParallelOptions> parametr a potom uzavřete paralelní volání do bloku try-catch.</span><span class="sxs-lookup"><span data-stu-id="7cb4e-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cb4e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="7cb4e-106">Example</span></span>  
 <span data-ttu-id="7cb4e-107">Následující příklad ukazuje, jak zrušit volání <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7cb4e-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7cb4e-108">Můžete použít ve stejný přístup k <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> volání.</span><span class="sxs-lookup"><span data-stu-id="7cb4e-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="7cb4e-109">Pokud je token, který signalizuje zrušení stejný token, který je určen v <xref:System.Threading.Tasks.ParallelOptions> instance, pak paralelní smyčky vyvolá jedinou <xref:System.OperationCanceledException> na zrušení.</span><span class="sxs-lookup"><span data-stu-id="7cb4e-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="7cb4e-110">Pokud jiný token zrušení způsobí, že opakování ve smyčce vyvolá <xref:System.AggregateException> s <xref:System.OperationCanceledException> jako InnerException.</span><span class="sxs-lookup"><span data-stu-id="7cb4e-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cb4e-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="7cb4e-111">See Also</span></span>  
 [<span data-ttu-id="7cb4e-112">Datový paralelismus</span><span class="sxs-lookup"><span data-stu-id="7cb4e-112">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="7cb4e-113">Výrazy lambda v PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="7cb4e-113">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
