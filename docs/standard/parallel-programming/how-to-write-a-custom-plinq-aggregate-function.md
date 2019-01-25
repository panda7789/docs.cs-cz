---
title: 'Postupy: Napsat vlastní agregační funkce pro PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03bbb9b7cf33eda1cc479759740e6c5325f635fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580665"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="579f7-102">Postupy: Napsat vlastní agregační funkce pro PLINQ</span><span class="sxs-lookup"><span data-stu-id="579f7-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="579f7-103">Tento příklad ukazuje způsob použití <xref:System.Linq.ParallelEnumerable.Aggregate%2A> způsob, jak použít vlastní agregační funkce zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="579f7-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="579f7-104">V tomto příkladu je za cíl předvést využití a nemusí pracovat rychleji než ekvivalentní sekvenčních LINQ to Objects dotazům.</span><span class="sxs-lookup"><span data-stu-id="579f7-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="579f7-105">Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="579f7-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="579f7-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="579f7-106">Example</span></span>  
 <span data-ttu-id="579f7-107">Následující příklad vypočítá směrodatnou odchylku posloupnost celých čísel.</span><span class="sxs-lookup"><span data-stu-id="579f7-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="579f7-108">Tento příklad používá přetížení operátoru standardního dotazu, které jsou jedinečné pro PLINQ.</span><span class="sxs-lookup"><span data-stu-id="579f7-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="579f7-109">Toto přetížení má speciální <xref:System.Func%603?displayProperty=nameWithType> jako třetí vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="579f7-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="579f7-110">Tento delegát kombinuje výsledky ze všech vláken, než provede konečné výpočtu na agregované výsledky.</span><span class="sxs-lookup"><span data-stu-id="579f7-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="579f7-111">V tomto příkladu jsme sečtení částek ze všech vláken.</span><span class="sxs-lookup"><span data-stu-id="579f7-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="579f7-112">Všimněte si, že tělo výrazu lambda sestává z jediného výrazu, návratová hodnota <xref:System.Func%602?displayProperty=nameWithType> delegát je hodnota výrazu.</span><span class="sxs-lookup"><span data-stu-id="579f7-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="579f7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="579f7-113">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="579f7-114">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="579f7-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
