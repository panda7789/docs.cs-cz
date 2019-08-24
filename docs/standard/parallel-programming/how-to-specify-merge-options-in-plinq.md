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
ms.openlocfilehash: 947f3cb15b7eb372d20884ece73374114c48f472
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988850"
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="2fc02-102">Postupy: Určení možností sloučení v PLINQ</span><span class="sxs-lookup"><span data-stu-id="2fc02-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="2fc02-103">Tento příklad ukazuje, jak určit možnosti sloučení, které budou použity pro všechny následné operátory v dotazu PLINQ.</span><span class="sxs-lookup"><span data-stu-id="2fc02-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="2fc02-104">Explicitně není nutné nastavovat možnosti sloučení, ale v takovém případě může dojít ke zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="2fc02-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="2fc02-105">Další informace o možnostech sloučení naleznete v tématu [možnosti sloučení v PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="2fc02-105">For more information about merge options, see [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="2fc02-106">Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz.</span><span class="sxs-lookup"><span data-stu-id="2fc02-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="2fc02-107">Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="2fc02-107">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fc02-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="2fc02-108">Example</span></span>  
 <span data-ttu-id="2fc02-109">Následující příklad ukazuje chování možností sloučení v základním scénáři, který má neuspořádaný zdroj a aplikuje nákladný funkce na každý prvek.</span><span class="sxs-lookup"><span data-stu-id="2fc02-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="2fc02-110">V případech, kdy <xref:System.Linq.ParallelMergeOptions.AutoBuffered> u možnosti dojde k nežádoucí latenci před dosažením prvního prvku, <xref:System.Linq.ParallelMergeOptions.NotBuffered> zkuste možnost vracet prvky výsledků rychleji a hladce.</span><span class="sxs-lookup"><span data-stu-id="2fc02-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fc02-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2fc02-111">See also</span></span>

- <xref:System.Linq.ParallelMergeOptions>
- [<span data-ttu-id="2fc02-112">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="2fc02-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
