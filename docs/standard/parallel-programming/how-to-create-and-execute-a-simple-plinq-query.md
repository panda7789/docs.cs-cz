---
title: "Postupy: Vytvoření a provedení jednoduchého dotazu PLINQ"
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
helpviewer_keywords: PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 20b1be451e53a81dd0631a89310a5b884aa83166
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="a3fb2-102">Postupy: Vytvoření a provedení jednoduchého dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="a3fb2-102">How to: Create and Execute a Simple PLINQ Query</span></span>
<span data-ttu-id="a3fb2-103">Následující příklad ukazuje, jak vytvořit jednoduchý dotaz paralelní LINQ pomocí <xref:System.Linq.ParallelEnumerable.AsParallel%2A> rozšiřující metody na zdrojové sekvence a provádění dotazu s použitím <xref:System.Linq.ParallelEnumerable.ForAll%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="a3fb2-103">The following example shows how to create a simple Parallel LINQ query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A> extension method on the source sequence, and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3fb2-104">Tato dokumentace používá k definování delegátů v PLINQ výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="a3fb2-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="a3fb2-105">Pokud nejste obeznámeni s výrazy lambda v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="a3fb2-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3fb2-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3fb2-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="a3fb2-107">Tento příklad ukazuje základní vzor pro vytváření a spouštění jakýkoli dotaz paralelní LINQ při řazení výsledků pořadí není důležité. Neseřazený dotazy jsou obecně rychlejší než seřazené dotazy.</span><span class="sxs-lookup"><span data-stu-id="a3fb2-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important; unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="a3fb2-108">Dotaz oddíly zdroje do úlohy, které se spustí asynchronně na více vláken.</span><span class="sxs-lookup"><span data-stu-id="a3fb2-108">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="a3fb2-109">Pořadí, ve kterém je každý úkol dokončí závisí nejen na objem práce související zpracovat elementy v oddílu, ale také na externí faktorech, například jak operačního systému plánuje každé vlákno.</span><span class="sxs-lookup"><span data-stu-id="a3fb2-109">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="a3fb2-110">Tento příklad je určený k předvedení využití a nemusí být možné spustit rychleji, než ekvivalentní sekvenčních LINQ na objekty dotazu.</span><span class="sxs-lookup"><span data-stu-id="a3fb2-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="a3fb2-111">Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="a3fb2-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="a3fb2-112">Další informace o tom, jak zachovat řazení elementů v dotazu najdete v tématu [postupy: řízení řazení v PLINQ dotazu](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="a3fb2-112">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3fb2-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3fb2-113">See Also</span></span>  
 [<span data-ttu-id="a3fb2-114">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="a3fb2-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
