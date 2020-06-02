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
ms.openlocfilehash: 644d6b6f929e040a0fe688c18c774de6f434c4b3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290769"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="f9682-102">Postupy: Psaní vlastní agregační funkce pro PLINQ</span><span class="sxs-lookup"><span data-stu-id="f9682-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="f9682-103">Tento příklad ukazuje, jak použít <xref:System.Linq.ParallelEnumerable.Aggregate%2A> metodu pro použití vlastní agregační funkce na zdrojovou sekvenci.</span><span class="sxs-lookup"><span data-stu-id="f9682-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="f9682-104">Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz.</span><span class="sxs-lookup"><span data-stu-id="f9682-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="f9682-105">Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="f9682-105">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9682-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9682-106">Example</span></span>  
 <span data-ttu-id="f9682-107">Následující příklad vypočítá směrodatnou odchylku posloupnosti celých čísel.</span><span class="sxs-lookup"><span data-stu-id="f9682-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="f9682-108">V tomto příkladu se používá přetížení agregačního standardního operátoru dotazu, který je jedinečný pro PLINQ.</span><span class="sxs-lookup"><span data-stu-id="f9682-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="f9682-109">Toto přetížení bere <xref:System.Func%603?displayProperty=nameWithType> jako třetí vstupní parametr extra.</span><span class="sxs-lookup"><span data-stu-id="f9682-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="f9682-110">Tento delegát kombinuje výsledky ze všech vláken předtím, než provede Konečný výpočet agregovaných výsledků.</span><span class="sxs-lookup"><span data-stu-id="f9682-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="f9682-111">V tomto příkladu přidáme součty ze všech vláken.</span><span class="sxs-lookup"><span data-stu-id="f9682-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="f9682-112">Všimněte si, že když tělo výrazu lambda se skládá z jednoho výrazu, návratová hodnota <xref:System.Func%602?displayProperty=nameWithType> delegáta je hodnota výrazu.</span><span class="sxs-lookup"><span data-stu-id="f9682-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9682-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9682-113">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="f9682-114">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="f9682-114">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
