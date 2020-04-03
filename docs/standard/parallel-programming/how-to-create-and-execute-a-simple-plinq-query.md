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
ms.openlocfilehash: c4cd75e55aabb551e5951a902ea6394a5659c9ee
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635856"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="36d05-102">Postupy: Vytvoření a provedení jednoduchého dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="36d05-102">How to: Create and Execute a Simple PLINQ Query</span></span>

<span data-ttu-id="36d05-103">Příklad v tomto článku ukazuje, jak vytvořit jednoduchý paralelní jazyk integrovaný <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> dotaz (LINQ) dotaz pomocí metody rozšíření <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithTyp> na zdrojové sekvence a provádění dotazu pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="36d05-103">The example in this article shows how to create a simple Parallel Language Integrated Query (LINQ) query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> extension method on the source sequence and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithTyp> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36d05-104">Tato dokumentace používá lambda výrazy definovat delegáty v PLINQ.</span><span class="sxs-lookup"><span data-stu-id="36d05-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="36d05-105">Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, naleznete [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="36d05-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="36d05-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="36d05-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="36d05-107">Tento příklad ukazuje základní vzor pro vytváření a provádění jakékoli paralelní LINQ dotazu při řazení pořadí výsledek sekvence není důležité.</span><span class="sxs-lookup"><span data-stu-id="36d05-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important.</span></span> <span data-ttu-id="36d05-108">Neuspořádané dotazy jsou obecně rychlejší než objednané dotazy.</span><span class="sxs-lookup"><span data-stu-id="36d05-108">Unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="36d05-109">Dotaz rozdělí zdroj do úloh, které jsou spouštěny asynchronně ve více vláknech.</span><span class="sxs-lookup"><span data-stu-id="36d05-109">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="36d05-110">Pořadí, ve kterém každý úkol dokončí závisí nejen na množství práce spojené se zpracováním prvků v oddílu, ale také na externí faktory, jako je například plánování operačního systému každé vlákno.</span><span class="sxs-lookup"><span data-stu-id="36d05-110">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="36d05-111">Tento příklad je určen k předvedení využití a nemusí běžet rychleji než ekvivalentní sekvenční LINQ na objekty dotazu.</span><span class="sxs-lookup"><span data-stu-id="36d05-111">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="36d05-112">Další informace o zrychlení naleznete v [tématu Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="36d05-112">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="36d05-113">Další informace o tom, jak zachovat řazení prvků v dotazu, naleznete v tématu [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="36d05-113">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d05-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="36d05-114">See also</span></span>

- [<span data-ttu-id="36d05-115">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="36d05-115">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
