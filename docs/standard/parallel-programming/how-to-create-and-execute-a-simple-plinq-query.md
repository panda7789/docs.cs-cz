---
title: 'Postupy: Vytvoření a provedení jednoduchého dotazu PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 472304dff23e92620dd461e8bc43c3093431ddc4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962521"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="1e69b-102">Postupy: Vytvoření a provedení jednoduchého dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="1e69b-102">How to: Create and Execute a Simple PLINQ Query</span></span>
<span data-ttu-id="1e69b-103">Následující příklad ukazuje, jak vytvořit jednoduchý paralelní dotaz LINQ pomocí <xref:System.Linq.ParallelEnumerable.AsParallel%2A> metody rozšíření zdrojové sekvence a provedení dotazu <xref:System.Linq.ParallelEnumerable.ForAll%2A> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="1e69b-103">The following example shows how to create a simple Parallel LINQ query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A> extension method on the source sequence, and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e69b-104">Tato dokumentace používá lambda výrazy k definování delegátů v PLINQ.</span><span class="sxs-lookup"><span data-stu-id="1e69b-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="1e69b-105">Pokud nejste obeznámeni s lambda výrazy v C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="1e69b-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e69b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e69b-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="1e69b-107">Tento příklad ukazuje základní vzor pro vytvoření a spuštění paralelního dotazu LINQ, pokud pořadí výsledků není důležité. neuspořádané dotazy jsou všeobecně rychlejší než seřazené dotazy.</span><span class="sxs-lookup"><span data-stu-id="1e69b-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important; unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="1e69b-108">Dotaz rozdělí zdroj na úlohy, které se provádějí asynchronně ve více vláknech.</span><span class="sxs-lookup"><span data-stu-id="1e69b-108">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="1e69b-109">Pořadí, ve kterém jednotlivé úlohy dokončí, závisí nejen na množství práce, která je součástí zpracování prvků v oddílu, ale také na vnějších faktorech, jako je například způsob, jakým operační systém naplánuje jednotlivá vlákna.</span><span class="sxs-lookup"><span data-stu-id="1e69b-109">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="1e69b-110">Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz.</span><span class="sxs-lookup"><span data-stu-id="1e69b-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="1e69b-111">Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="1e69b-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="1e69b-112">Další informace o tom, jak zachovat řazení prvků v dotazu, naleznete v tématu [How to: Řazení ovládacích prvků v dotazu](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)PLINQ.</span><span class="sxs-lookup"><span data-stu-id="1e69b-112">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e69b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e69b-113">See also</span></span>

- [<span data-ttu-id="1e69b-114">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="1e69b-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
