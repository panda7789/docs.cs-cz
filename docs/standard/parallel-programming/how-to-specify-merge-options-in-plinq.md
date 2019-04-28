---
title: 'Postupy: Určení možností sloučení v PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87079337ae3cea81dbb4aab13ec2043b74498d9a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672702"
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="96559-102">Postupy: Určení možností sloučení v PLINQ</span><span class="sxs-lookup"><span data-stu-id="96559-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="96559-103">Tento příklad ukazuje postup určení možností sloučení, které budou platit pro všechny následující operátory v dotazu PLINQ.</span><span class="sxs-lookup"><span data-stu-id="96559-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="96559-104">Není nutné explicitně nastavit možnosti sloučení, ale to může zlepšit výkon.</span><span class="sxs-lookup"><span data-stu-id="96559-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="96559-105">Další informace o možnosti sloučení, naleznete v tématu [možností sloučení v PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="96559-105">For more information about merge options, see [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="96559-106">V tomto příkladu je za cíl předvést využití a nemusí pracovat rychleji než ekvivalentní sekvenčních LINQ to Objects dotazům.</span><span class="sxs-lookup"><span data-stu-id="96559-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="96559-107">Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="96559-107">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="96559-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="96559-108">Example</span></span>  
 <span data-ttu-id="96559-109">Následující příklad ukazuje chování možnosti sloučení v základní scénář, který obsahuje Neseřazený zdroj a nákladná funkce se vztahuje na každý prvek.</span><span class="sxs-lookup"><span data-stu-id="96559-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="96559-110">V případech, kde <xref:System.Linq.ParallelMergeOptions.AutoBuffered> možnost způsobuje nežádoucí zpoždění před první prvek, je vhodné, zkuste <xref:System.Linq.ParallelMergeOptions.NotBuffered> možnost pro získání výsledku prvků rychleji a plynuleji.</span><span class="sxs-lookup"><span data-stu-id="96559-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96559-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96559-111">See also</span></span>

- <xref:System.Linq.ParallelMergeOptions>
- [<span data-ttu-id="96559-112">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="96559-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
