---
title: 'Postupy: Implementace rozdělovače pro statické dělení'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 22d2cf788d4726488512703356a75f84efd04250
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278503"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="ceea8-102">Postupy: Implementace rozdělovače pro statické dělení</span><span class="sxs-lookup"><span data-stu-id="ceea8-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="ceea8-103">Následující příklad ukazuje jeden ze způsobů implementace jednoduchého vlastního rozdělovače pro PLINQ, který provádí statické dělení.</span><span class="sxs-lookup"><span data-stu-id="ceea8-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="ceea8-104">Protože dělicí metoda nepodporuje dynamické oddíly, není z nich spotřební <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ceea8-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ceea8-105">Tento konkrétní rozdělovač může poskytovat zrychlení prostřednictvím výchozího dělicího oddílu rozsahu pro zdroje dat, pro které každý prvek vyžaduje větší množství času zpracování.</span><span class="sxs-lookup"><span data-stu-id="ceea8-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ceea8-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ceea8-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="ceea8-107">Oddíly v tomto příkladu jsou založeny na předpokladu lineárního nárůstu doby zpracování každého prvku.</span><span class="sxs-lookup"><span data-stu-id="ceea8-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="ceea8-108">V reálném světě může být obtížné odhadnout dobu zpracování tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="ceea8-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="ceea8-109">Pokud používáte statický dělicí modul s konkrétním zdrojem dat, můžete optimalizovat vzorec dělení zdroje, přidat logiku vyrovnávání zatížení nebo použít přístup k dělení bloků dat, jak je znázorněno v tématu [Postupy: Implementace dynamických oddílů](how-to-implement-dynamic-partitions.md).</span><span class="sxs-lookup"><span data-stu-id="ceea8-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceea8-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="ceea8-110">See also</span></span>

- [<span data-ttu-id="ceea8-111">Vlastní dělicí metody pro PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="ceea8-111">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
