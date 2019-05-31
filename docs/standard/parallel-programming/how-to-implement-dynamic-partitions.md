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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5719c6afc1c5efc6138f0a4931d1725a6f20909a
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66424047"
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="21fcc-102">Postupy: Implementace dynamických oddílů</span><span class="sxs-lookup"><span data-stu-id="21fcc-102">How to: Implement Dynamic Partitions</span></span>

<span data-ttu-id="21fcc-103">Následující příklad ukazuje, jak implementovat vlastní <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> , který implementuje dynamické dělení na oddíly a je možné z určité přetížení <xref:System.Threading.Tasks.Parallel.ForEach%2A> a PLINQ.</span><span class="sxs-lookup"><span data-stu-id="21fcc-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21fcc-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="21fcc-104">Example</span></span>

<span data-ttu-id="21fcc-105">Pokaždé, když volá oddílu <xref:System.Collections.IEnumerator.MoveNext%2A> v čítači výčtu, enumerátor obsahuje oddíl s elementem jeden seznam.</span><span class="sxs-lookup"><span data-stu-id="21fcc-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="21fcc-106">V případě PLINQ a <xref:System.Threading.Tasks.Parallel.ForEach%2A>, je oddíl <xref:System.Threading.Tasks.Task> instance.</span><span class="sxs-lookup"><span data-stu-id="21fcc-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="21fcc-107">Protože požadavky se dějí souběžně na několika vláknech, se synchronizuje přístup k aktuální index.</span><span class="sxs-lookup"><span data-stu-id="21fcc-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

<span data-ttu-id="21fcc-108">Toto je příklad bloků dělení každý blok, který se skládá z jednoho prvku.</span><span class="sxs-lookup"><span data-stu-id="21fcc-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="21fcc-109">Tím, že poskytuje další elementy v čase, můžete omezit kolize přes zámek a teoreticky dosáhnout vyššího výkonu.</span><span class="sxs-lookup"><span data-stu-id="21fcc-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="21fcc-110">Ale v určitém okamžiku větší bloky vyžadovat další logiku vyrovnávání zatížení aby bylo možné udržovat zaneprázdněný všechna vlákna, dokud se provádí veškerou práci.</span><span class="sxs-lookup"><span data-stu-id="21fcc-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21fcc-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21fcc-111">See also</span></span>

* [<span data-ttu-id="21fcc-112">Vlastní dělicí metody pro PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="21fcc-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
* [<span data-ttu-id="21fcc-113">Postupy: Implementace rozdělovače pro statické dělení</span><span class="sxs-lookup"><span data-stu-id="21fcc-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
