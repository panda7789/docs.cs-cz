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
ms.openlocfilehash: e98ede3664a8815c60a490239a789c69fa557895
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588563"
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="343f8-102">Postupy: Určení možností sloučení v PLINQ</span><span class="sxs-lookup"><span data-stu-id="343f8-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="343f8-103">Tento příklad ukazuje, jak určit možnosti sloučení, které se budou vztahovat na všechny následné operátory v dotazu PLINQ.</span><span class="sxs-lookup"><span data-stu-id="343f8-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="343f8-104">Není třeba explicitně nastavit možnosti sloučení, ale to může zlepšit výkon.</span><span class="sxs-lookup"><span data-stu-id="343f8-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="343f8-105">Další informace o možnostech sloučení naleznete [v tématu Sloučit možnosti v plinq](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="343f8-105">For more information about merge options, see [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="343f8-106">Tento příklad je určen k předvedení využití a nemusí běžet rychleji než ekvivalentní sekvenční LINQ na objekty dotazu.</span><span class="sxs-lookup"><span data-stu-id="343f8-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="343f8-107">Další informace o zrychlení naleznete v [tématu Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="343f8-107">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="343f8-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="343f8-108">Example</span></span>  
 <span data-ttu-id="343f8-109">Následující příklad ukazuje chování možností sloučení v základním scénáři, který má neuspořádaný zdroj a použije nákladné funkce pro každý prvek.</span><span class="sxs-lookup"><span data-stu-id="343f8-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="343f8-110">V případech, <xref:System.Linq.ParallelMergeOptions.AutoBuffered> kdy možnost vznikne nežádoucí latence před první prvek <xref:System.Linq.ParallelMergeOptions.NotBuffered> je výnosný, zkuste možnost výnos u datovat prvky výsledku rychleji a plynuleji.</span><span class="sxs-lookup"><span data-stu-id="343f8-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="343f8-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="343f8-111">See also</span></span>

- <xref:System.Linq.ParallelMergeOptions>
- [<span data-ttu-id="343f8-112">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="343f8-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
