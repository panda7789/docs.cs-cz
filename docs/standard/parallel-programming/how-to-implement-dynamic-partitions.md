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
ms.openlocfilehash: 197e71cf4f00c98891e58e5f72974c0ec407e6ce
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288443"
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="cf9c9-102">Postupy: Implementace dynamických oddílů</span><span class="sxs-lookup"><span data-stu-id="cf9c9-102">How to: Implement Dynamic Partitions</span></span>

<span data-ttu-id="cf9c9-103">Následující příklad ukazuje, jak implementovat vlastní <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> , který implementuje dynamické dělení a lze jej použít z určitých přetížení <xref:System.Threading.Tasks.Parallel.ForEach%2A> a z PLINQ.</span><span class="sxs-lookup"><span data-stu-id="cf9c9-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf9c9-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="cf9c9-104">Example</span></span>

<span data-ttu-id="cf9c9-105">Pokaždé, když oddíl volá <xref:System.Collections.IEnumerator.MoveNext%2A> na enumerátor, enumerátor poskytuje oddíl s jedním seznamem elementů.</span><span class="sxs-lookup"><span data-stu-id="cf9c9-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="cf9c9-106">V případě PLINQ a <xref:System.Threading.Tasks.Parallel.ForEach%2A> je oddíl <xref:System.Threading.Tasks.Task> instancí.</span><span class="sxs-lookup"><span data-stu-id="cf9c9-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="cf9c9-107">Vzhledem k tomu, že žádosti jsou souběžně na více vláknech, je přístup k aktuálnímu indexu synchronizovaný.</span><span class="sxs-lookup"><span data-stu-id="cf9c9-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

<span data-ttu-id="cf9c9-108">Toto je příklad dělení bloků dat s každým blokem, který se skládá z jednoho prvku.</span><span class="sxs-lookup"><span data-stu-id="cf9c9-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="cf9c9-109">Poskytnutím více prvků v čase můžete snížit kolizí přes zámek a teoreticky dosáhnout rychlejšího výkonu.</span><span class="sxs-lookup"><span data-stu-id="cf9c9-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="cf9c9-110">V některých případech ale větší počet bloků může vyžadovat další logiku vyrovnávání zatížení, aby všechna vlákna byla zaneprázdněná, dokud neproběhne veškerá práce.</span><span class="sxs-lookup"><span data-stu-id="cf9c9-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf9c9-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf9c9-111">See also</span></span>

* [<span data-ttu-id="cf9c9-112">Vlastní dělicí metody pro PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="cf9c9-112">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
* [<span data-ttu-id="cf9c9-113">Postupy: Implementace rozdělovače pro statické dělení</span><span class="sxs-lookup"><span data-stu-id="cf9c9-113">How to: Implement a Partitioner for Static Partitioning</span></span>](how-to-implement-a-partitioner-for-static-partitioning.md)
