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
ms.openlocfilehash: 544ea0f89dfa518c2ef18bffe2609d72e6fdee70
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891217"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="dacc6-102">Postupy: Vytvoření a provedení jednoduchého dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="dacc6-102">How to: Create and Execute a Simple PLINQ Query</span></span>
<span data-ttu-id="dacc6-103">Následující příklad ukazuje, jak vytvořit jednoduchý dotaz paralelní LINQ pomocí <xref:System.Linq.ParallelEnumerable.AsParallel%2A> rozšiřující metody na zdrojové sekvence a pomocí provádí dotaz <xref:System.Linq.ParallelEnumerable.ForAll%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="dacc6-103">The following example shows how to create a simple Parallel LINQ query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A> extension method on the source sequence, and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dacc6-104">Tato dokumentace používá lambda výrazy k definování delegátů v PLINQ.</span><span class="sxs-lookup"><span data-stu-id="dacc6-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="dacc6-105">Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="dacc6-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dacc6-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="dacc6-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="dacc6-107">Tento příklad ukazuje základní vzor pro vytváření a spouštění jakéhokoli paralelní LINQ dotazu při řazení výsledků pořadí není důležité. Neseřazený dotazy jsou obecně rychlejší než uspořádaných dotazů.</span><span class="sxs-lookup"><span data-stu-id="dacc6-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important; unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="dacc6-108">Dotaz oddíly zdroje do úlohy, které se provedl asynchronně při více vláken.</span><span class="sxs-lookup"><span data-stu-id="dacc6-108">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="dacc6-109">Pořadí, ve kterém každý úkol dokončí závisí nejen objem práce související zpracování elementů v oddílu, ale také externí faktory, jako je například jak operačního systému plánuje každé vlákno.</span><span class="sxs-lookup"><span data-stu-id="dacc6-109">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="dacc6-110">V tomto příkladu je za cíl předvést využití a nemusí pracovat rychleji než ekvivalentní sekvenčních LINQ to Objects dotazům.</span><span class="sxs-lookup"><span data-stu-id="dacc6-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="dacc6-111">Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="dacc6-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="dacc6-112">Další informace o tom, jak zachovat pořadí prvků v dotazu naleznete v tématu [postupy: řízení řazení v dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="dacc6-112">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dacc6-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dacc6-113">See also</span></span>

- [<span data-ttu-id="dacc6-114">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="dacc6-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
