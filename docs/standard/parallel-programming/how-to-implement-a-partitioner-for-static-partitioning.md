---
title: "Postupy: Implementace rozdělovače pro statické dělení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 125bef8d43e16c120e88250a4d9d5a4ff3f63dba
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="09164-102">Postupy: Implementace rozdělovače pro statické dělení</span><span class="sxs-lookup"><span data-stu-id="09164-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="09164-103">Následující příklad ukazuje jeden způsob, jak implementovat jednoduchý vlastní dělicí metody pro PLINQ, který provádí statické dělení.</span><span class="sxs-lookup"><span data-stu-id="09164-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="09164-104">Protože dělicí metody nepodporuje dynamických oddílů, není použití z <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09164-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="09164-105">Tato konkrétní rozdělovač může být rychlejší přes výchozí rozdělovač zdroje dat, pro které každý prvek vyžaduje roste množství doba zpracování.</span><span class="sxs-lookup"><span data-stu-id="09164-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09164-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="09164-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="09164-107">Oddíly v tomto příkladu jsou založené na předpokladu lineární nárůst doba zpracování pro jednotlivé elementy.</span><span class="sxs-lookup"><span data-stu-id="09164-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="09164-108">V praxi může být obtížné odhadnout časy zpracování tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="09164-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="09164-109">Pokud používáte statické dělicí metody s konkrétní zdroj dat., můžete optimalizovat rozdělení vzorec pro zdroj, přidejte logiku vyrovnávání zatížení nebo použijte dělení způsob, jak je předvedeno v bloku dat [postupy: implementace dynamických oddílů](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span><span class="sxs-lookup"><span data-stu-id="09164-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09164-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="09164-110">See Also</span></span>  
 [<span data-ttu-id="09164-111">Vlastní dělicí metody pro PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="09164-111">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
