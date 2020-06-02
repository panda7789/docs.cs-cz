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
ms.openlocfilehash: a9c044254423d0f9d266539c728a6604f562e97d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290003"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="03a63-102">Postupy: Vytvoření a provedení jednoduchého dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="03a63-102">How to: Create and Execute a Simple PLINQ Query</span></span>

<span data-ttu-id="03a63-103">Příklad v tomto článku ukazuje, jak vytvořit jednoduchý dotaz LINQ (paralelní jazyk Integrated Query) pomocí <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> metody rozšíření ve zdrojové sekvenci a provedení dotazu pomocí <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithTyp> metody.</span><span class="sxs-lookup"><span data-stu-id="03a63-103">The example in this article shows how to create a simple Parallel Language Integrated Query (LINQ) query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> extension method on the source sequence and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithTyp> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="03a63-104">Tato dokumentace používá lambda výrazy k definování delegátů v PLINQ.</span><span class="sxs-lookup"><span data-stu-id="03a63-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="03a63-105">Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="03a63-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="03a63-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="03a63-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="03a63-107">Tento příklad ukazuje základní vzor pro vytvoření a spuštění paralelního dotazu LINQ, pokud pořadí výsledků není důležité.</span><span class="sxs-lookup"><span data-stu-id="03a63-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important.</span></span> <span data-ttu-id="03a63-108">Neuspořádané dotazy jsou všeobecně rychlejší než seřazené dotazy.</span><span class="sxs-lookup"><span data-stu-id="03a63-108">Unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="03a63-109">Dotaz rozdělí zdroj na úlohy, které se provádějí asynchronně ve více vláknech.</span><span class="sxs-lookup"><span data-stu-id="03a63-109">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="03a63-110">Pořadí, ve kterém jednotlivé úlohy dokončí, závisí nejen na množství práce, která je součástí zpracování prvků v oddílu, ale také na vnějších faktorech, jako je například způsob, jakým operační systém naplánuje jednotlivá vlákna.</span><span class="sxs-lookup"><span data-stu-id="03a63-110">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="03a63-111">Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz.</span><span class="sxs-lookup"><span data-stu-id="03a63-111">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="03a63-112">Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="03a63-112">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="03a63-113">Další informace o tom, jak zachovat řazení prvků v dotazu, naleznete v tématu [How to: Order Control in a PLINQ Query](how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="03a63-113">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a63-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="03a63-114">See also</span></span>

- [<span data-ttu-id="03a63-115">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="03a63-115">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
