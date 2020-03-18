---
title: 'Postupy: Implementace rozdělovače pro statické dělení'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 94fbb681b20b9c920c20df2a9017f75a9aa9a6ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091521"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="7e499-102">Postupy: Implementace rozdělovače pro statické dělení</span><span class="sxs-lookup"><span data-stu-id="7e499-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="7e499-103">Následující příklad ukazuje jeden způsob, jak implementovat jednoduchý vlastní partitioner pro PLINQ, který provádí statické dělení.</span><span class="sxs-lookup"><span data-stu-id="7e499-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="7e499-104">Vzhledem k tomu, že rozdělovač nepodporuje dynamické <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>oddíly, není spotřební mj.</span><span class="sxs-lookup"><span data-stu-id="7e499-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7e499-105">Tento konkrétní rozdělovač může poskytnout zrychlení přes výchozí rozsah partitioner pro zdroje dat, pro které každý prvek vyžaduje rostoucí množství času zpracování.</span><span class="sxs-lookup"><span data-stu-id="7e499-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e499-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e499-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="7e499-107">Oddíly v tomto příkladu jsou založeny na předpokladu lineární zvýšení doby zpracování pro každý prvek.</span><span class="sxs-lookup"><span data-stu-id="7e499-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="7e499-108">V reálném světě může být obtížné předpovědět časy zpracování tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="7e499-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="7e499-109">Pokud používáte statický rozdělovač s určitým zdrojem dat, můžete optimalizovat vzorec dělení pro zdroj, přidat logiku vyrovnávání zatížení nebo použít přístup dělení bloku, jak je znázorněno v [postupech: Implementace dynamických oddílů](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span><span class="sxs-lookup"><span data-stu-id="7e499-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e499-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e499-110">See also</span></span>

- [<span data-ttu-id="7e499-111">Vlastní dělicí metody pro PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="7e499-111">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
