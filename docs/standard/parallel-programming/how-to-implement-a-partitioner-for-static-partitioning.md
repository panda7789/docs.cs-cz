---
title: 'Postupy: Implementace rozdělovače pro statické dělení'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 302d7d98d04e528d205edf38c3fa13bb3f2b2252
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638256"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="6196f-102">Postupy: Implementace rozdělovače pro statické dělení</span><span class="sxs-lookup"><span data-stu-id="6196f-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="6196f-103">Následující příklad ukazuje jeden způsob, jak implementovat jednoduché vlastní dělicí metody pro PLINQ, který provádí statické dělení.</span><span class="sxs-lookup"><span data-stu-id="6196f-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="6196f-104">Vzhledem k tomu dělicí metoda nepodporuje dynamické oddíly, není použitelné z <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6196f-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6196f-105">Tento konkrétní rozdělovač může být rychlejší nad výchozí rozdělovač pro zdroje dat, u kterých každý prvek vyžaduje zvýšení množství času procesoru.</span><span class="sxs-lookup"><span data-stu-id="6196f-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6196f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6196f-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="6196f-107">Oddíly v tomto příkladu jsou založeny na předpokladu lineární zvýšení doba zpracování pro každý prvek.</span><span class="sxs-lookup"><span data-stu-id="6196f-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="6196f-108">V praxi může být obtížné odhadnout časy zpracování tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="6196f-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="6196f-109">Pokud používáte statické dělicí metody s konkrétnímu zdroji dat, můžete optimalizovat dělení vzorce pro zdroj, přidejte logiku pro vyrovnávání zatížení nebo použít blok dělení přístup, jak je ukázáno v [jak: Implementace dynamických oddílů](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span><span class="sxs-lookup"><span data-stu-id="6196f-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6196f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6196f-110">See also</span></span>

- [<span data-ttu-id="6196f-111">Vlastní dělicí metody pro PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="6196f-111">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
