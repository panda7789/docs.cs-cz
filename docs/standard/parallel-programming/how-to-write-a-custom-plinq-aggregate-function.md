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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106759"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="ca22b-102">Postupy: Psaní vlastní agregační funkce pro PLINQ</span><span class="sxs-lookup"><span data-stu-id="ca22b-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="ca22b-103">Tento příklad ukazuje, jak použít metodu <xref:System.Linq.ParallelEnumerable.Aggregate%2A> pro použití vlastní agregační funkce na zdrojovou sekvenci.</span><span class="sxs-lookup"><span data-stu-id="ca22b-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="ca22b-104">Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz.</span><span class="sxs-lookup"><span data-stu-id="ca22b-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="ca22b-105">Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="ca22b-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca22b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ca22b-106">Example</span></span>  
 <span data-ttu-id="ca22b-107">Následující příklad vypočítá směrodatnou odchylku posloupnosti celých čísel.</span><span class="sxs-lookup"><span data-stu-id="ca22b-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="ca22b-108">V tomto příkladu se používá přetížení agregačního standardního operátoru dotazu, který je jedinečný pro PLINQ.</span><span class="sxs-lookup"><span data-stu-id="ca22b-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="ca22b-109">Toto přetížení vezme další <xref:System.Func%603?displayProperty=nameWithType> jako třetí vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="ca22b-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="ca22b-110">Tento delegát kombinuje výsledky ze všech vláken předtím, než provede Konečný výpočet agregovaných výsledků.</span><span class="sxs-lookup"><span data-stu-id="ca22b-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="ca22b-111">V tomto příkladu přidáme součty ze všech vláken.</span><span class="sxs-lookup"><span data-stu-id="ca22b-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="ca22b-112">Všimněte si, že když tělo výrazu lambda se skládá z jednoho výrazu, návratová hodnota delegáta <xref:System.Func%602?displayProperty=nameWithType> je hodnota výrazu.</span><span class="sxs-lookup"><span data-stu-id="ca22b-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca22b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca22b-113">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="ca22b-114">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="ca22b-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
