---
title: 'Postupy: Implementace dynamických oddílů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
ms.openlocfilehash: 3970566b4e3f51ce538c328d4e69b20ec22ec09b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091423"
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="80429-102">Postupy: Implementace dynamických oddílů</span><span class="sxs-lookup"><span data-stu-id="80429-102">How to: Implement Dynamic Partitions</span></span>

<span data-ttu-id="80429-103">Následující příklad ukazuje, jak <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> implementovat vlastní, který implementuje dynamické <xref:System.Threading.Tasks.Parallel.ForEach%2A> dělení a lze použít z určitých přetížení a z PLINQ.</span><span class="sxs-lookup"><span data-stu-id="80429-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80429-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="80429-104">Example</span></span>

<span data-ttu-id="80429-105">Pokaždé, když <xref:System.Collections.IEnumerator.MoveNext%2A> oddíl volá čítače výčtu, čítač výčtu poskytuje oddíl s jedním list element.</span><span class="sxs-lookup"><span data-stu-id="80429-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="80429-106">V případě PLINQ <xref:System.Threading.Tasks.Parallel.ForEach%2A>a , oddíl <xref:System.Threading.Tasks.Task> je instance.</span><span class="sxs-lookup"><span data-stu-id="80429-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="80429-107">Vzhledem k tomu, že požadavky probíhají souběžně ve více vláknech, je synchronizován přístup k aktuálnímu indexu.</span><span class="sxs-lookup"><span data-stu-id="80429-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

<span data-ttu-id="80429-108">Toto je příklad rozdělení bloku, přičemž každý blok se skládá z jednoho prvku.</span><span class="sxs-lookup"><span data-stu-id="80429-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="80429-109">Poskytnutím více prvků najednou, můžete snížit konflikty přes zámek a teoreticky dosáhnout vyššího výkonu.</span><span class="sxs-lookup"><span data-stu-id="80429-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="80429-110">V určitém okamžiku však větší bloky mohou vyžadovat další logiku vyrovnávání zatížení, aby byla všechna vlákna zaneprázdněna, dokud nebude provedena veškerá práce.</span><span class="sxs-lookup"><span data-stu-id="80429-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80429-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="80429-111">See also</span></span>

* [<span data-ttu-id="80429-112">Vlastní dělicí metody pro PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="80429-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
* [<span data-ttu-id="80429-113">Postupy: Implementace rozdělovače pro statické dělení</span><span class="sxs-lookup"><span data-stu-id="80429-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
