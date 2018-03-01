---
title: "Postupy: Psaní vlastní agregační funkce pro PLINQ"
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
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 210e9913ab3eba636ff99b7610df05655246f4eb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="ac95e-102">Postupy: Psaní vlastní agregační funkce pro PLINQ</span><span class="sxs-lookup"><span data-stu-id="ac95e-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="ac95e-103">Tento příklad ukazuje způsob použití <xref:System.Linq.ParallelEnumerable.Aggregate%2A> metodu chcete použít vlastní agregační funkce pro zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="ac95e-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ac95e-104">Tento příklad je určený k předvedení využití a nemusí být možné spustit rychleji, než ekvivalentní sekvenčních LINQ na objekty dotazu.</span><span class="sxs-lookup"><span data-stu-id="ac95e-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="ac95e-105">Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="ac95e-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac95e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac95e-106">Example</span></span>  
 <span data-ttu-id="ac95e-107">Následující příklad vypočítá směrodatnou odchylku posloupnost celých čísel.</span><span class="sxs-lookup"><span data-stu-id="ac95e-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="ac95e-108">Tento příklad používá přetížení operátoru agregační standardní dotazu, které jsou jedinečné pro PLINQ.</span><span class="sxs-lookup"><span data-stu-id="ac95e-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="ac95e-109">Toto přetížení trvá Další <xref:System.Func%603?displayProperty=nameWithType> třetí vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="ac95e-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="ac95e-110">Tento delegát kombinuje výsledky z všechna vlákna, než provede konečný výpočet na agregované výsledky.</span><span class="sxs-lookup"><span data-stu-id="ac95e-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="ac95e-111">V tomto příkladu přidáme společně součtů ze všech vláken.</span><span class="sxs-lookup"><span data-stu-id="ac95e-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="ac95e-112">Všimněte si, že pokud lambda výraz sestává z jediného výrazu, vrátí hodnotu, která <xref:System.Func%602?displayProperty=nameWithType> delegáta je hodnota výrazu.</span><span class="sxs-lookup"><span data-stu-id="ac95e-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac95e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac95e-113">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="ac95e-114">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="ac95e-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
