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
ms.openlocfilehash: 84667fa1fbe2966c580d9c6d32e52ed686af7bb3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288118"
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="5a584-102">Postupy: Určení možností sloučení v PLINQ</span><span class="sxs-lookup"><span data-stu-id="5a584-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="5a584-103">Tento příklad ukazuje, jak určit možnosti sloučení, které budou použity pro všechny následné operátory v dotazu PLINQ.</span><span class="sxs-lookup"><span data-stu-id="5a584-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="5a584-104">Explicitně není nutné nastavovat možnosti sloučení, ale v takovém případě může dojít ke zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="5a584-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="5a584-105">Další informace o možnostech sloučení naleznete v tématu [možnosti sloučení v PLINQ](merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="5a584-105">For more information about merge options, see [Merge Options in PLINQ](merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="5a584-106">Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz.</span><span class="sxs-lookup"><span data-stu-id="5a584-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="5a584-107">Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="5a584-107">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a584-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a584-108">Example</span></span>  
 <span data-ttu-id="5a584-109">Následující příklad ukazuje chování možností sloučení v základním scénáři, který má neuspořádaný zdroj a aplikuje nákladný funkce na každý prvek.</span><span class="sxs-lookup"><span data-stu-id="5a584-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="5a584-110">V případech, kdy u <xref:System.Linq.ParallelMergeOptions.AutoBuffered> Možnosti dojde k nežádoucí latenci před dosažením prvního prvku, zkuste <xref:System.Linq.ParallelMergeOptions.NotBuffered> možnost vracet prvky výsledků rychleji a hladce.</span><span class="sxs-lookup"><span data-stu-id="5a584-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a584-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a584-111">See also</span></span>

- <xref:System.Linq.ParallelMergeOptions>
- [<span data-ttu-id="5a584-112">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="5a584-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
