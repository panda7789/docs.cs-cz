---
title: "Postupy: Určení možností sloučení v PLINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 59ffff3019f10874bd2df977b80d46e903d13613
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="47ec2-102">Postupy: Určení možností sloučení v PLINQ</span><span class="sxs-lookup"><span data-stu-id="47ec2-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="47ec2-103">Tento příklad ukazuje postup určení možností sloučení, které se použijí na všechny následné operátory v PLINQ dotazu.</span><span class="sxs-lookup"><span data-stu-id="47ec2-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="47ec2-104">Není nutné explicitně nastavit možnosti sloučení, ale to může zvýšit výkon.</span><span class="sxs-lookup"><span data-stu-id="47ec2-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="47ec2-105">Další informace o možnostech sloučení najdete v tématu [možností sloučení v PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="47ec2-105">For more information about merge options, see [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="47ec2-106">Tento příklad je určený k předvedení využití a nemusí být možné spustit rychleji, než ekvivalentní sekvenčních LINQ na objekty dotazu.</span><span class="sxs-lookup"><span data-stu-id="47ec2-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="47ec2-107">Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="47ec2-107">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="47ec2-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="47ec2-108">Example</span></span>  
 <span data-ttu-id="47ec2-109">Následující příklad ukazuje chování možností sloučení v základní scénáře, který je neuspořádaného zdroje a nákladné funkce se vztahuje na každý element.</span><span class="sxs-lookup"><span data-stu-id="47ec2-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="47ec2-110">V případech, kde <xref:System.Linq.ParallelMergeOptions.AutoBuffered> možnost způsobuje nežádoucí zpoždění před první prvek, je vhodné, zkuste <xref:System.Linq.ParallelMergeOptions.NotBuffered> možnost pro získání výsledných prvků rychleji a více plynule.</span><span class="sxs-lookup"><span data-stu-id="47ec2-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47ec2-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="47ec2-111">See Also</span></span>  
 <xref:System.Linq.ParallelMergeOptions>  
 [<span data-ttu-id="47ec2-112">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="47ec2-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
