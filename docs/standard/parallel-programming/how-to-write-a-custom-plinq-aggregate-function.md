---
title: 'Postupy: Psaní vlastní agregační funkce pro PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
ms.openlocfilehash: 7bb4cc1b69f0b6b97c1cf6255ded5341304f3ee3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106759"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="4b12f-102">Postupy: Psaní vlastní agregační funkce pro PLINQ</span><span class="sxs-lookup"><span data-stu-id="4b12f-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="4b12f-103">Tento příklad ukazuje, <xref:System.Linq.ParallelEnumerable.Aggregate%2A> jak použít metodu použít vlastní agregaci funkce zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="4b12f-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="4b12f-104">Tento příklad je určen k předvedení využití a nemusí běžet rychleji než ekvivalentní sekvenční LINQ na objekty dotazu.</span><span class="sxs-lookup"><span data-stu-id="4b12f-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="4b12f-105">Další informace o zrychlení naleznete v [tématu Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="4b12f-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b12f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b12f-106">Example</span></span>  
 <span data-ttu-id="4b12f-107">Následující příklad vypočítá směrodatnou odchylku posloupnosti celá čísla.</span><span class="sxs-lookup"><span data-stu-id="4b12f-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="4b12f-108">Tento příklad používá přetížení operátoru standardní dotaz, který je jedinečný pro PLINQ.</span><span class="sxs-lookup"><span data-stu-id="4b12f-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="4b12f-109">Toto přetížení <xref:System.Func%603?displayProperty=nameWithType> trvá extra jako třetí vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="4b12f-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="4b12f-110">Tento delegát kombinuje výsledky ze všech vláken před provedením konečného výpočtu na agregované výsledky.</span><span class="sxs-lookup"><span data-stu-id="4b12f-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="4b12f-111">V tomto příkladu sečteme součty ze všech vláken.</span><span class="sxs-lookup"><span data-stu-id="4b12f-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="4b12f-112">Všimněte si, že když lambda tělo výrazu se <xref:System.Func%602?displayProperty=nameWithType> skládá z jednoho výrazu, vrácená hodnota delegáta je hodnota výrazu.</span><span class="sxs-lookup"><span data-stu-id="4b12f-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b12f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b12f-113">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="4b12f-114">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="4b12f-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
