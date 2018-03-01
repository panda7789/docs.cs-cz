---
title: "Postupy: Implementace dynamických oddílů"
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
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9b08c387c9b10a9d6fa8728a7fce87a7894a37fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="3c2c0-102">Postupy: Implementace dynamických oddílů</span><span class="sxs-lookup"><span data-stu-id="3c2c0-102">How to: Implement Dynamic Partitions</span></span>
<span data-ttu-id="3c2c0-103">Následující příklad ukazuje, jak implementovat vlastní <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> , implementuje dynamické rozdělení a dá se použít z určité přetížení <xref:System.Threading.Tasks.Parallel.ForEach%2A> a PLINQ.</span><span class="sxs-lookup"><span data-stu-id="3c2c0-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c2c0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c2c0-104">Example</span></span>  
 <span data-ttu-id="3c2c0-105">Pokaždé, když oddíl volá <xref:System.Collections.IEnumerator.MoveNext%2A> na enumerátor, enumerátor poskytuje oddílu jeden element ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="3c2c0-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="3c2c0-106">V případě PLINQ a <xref:System.Threading.Tasks.Parallel.ForEach%2A>, zda je oddíl <xref:System.Threading.Tasks.Task> instance.</span><span class="sxs-lookup"><span data-stu-id="3c2c0-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="3c2c0-107">Protože požadavky se dějí souběžně na více vláken, přístup k aktuální index je synchronizován.</span><span class="sxs-lookup"><span data-stu-id="3c2c0-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 <span data-ttu-id="3c2c0-108">Toto je příklad bloku rozdělení do oddílů s každého bloku, který se skládá z jeden element.</span><span class="sxs-lookup"><span data-stu-id="3c2c0-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="3c2c0-109">Tím, že poskytuje další prvky současně, můžete snížit boj zámek a teoreticky dosáhnout vyšší výkon.</span><span class="sxs-lookup"><span data-stu-id="3c2c0-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="3c2c0-110">Ale v určitém okamžiku větší bloky vyžadovat další vyrovnávání zátěže abychom zachovali všechna vlákna zaneprázdněný, dokud všechny práci.</span><span class="sxs-lookup"><span data-stu-id="3c2c0-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c2c0-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c2c0-111">See Also</span></span>  
 [<span data-ttu-id="3c2c0-112">Vlastní dělicí metody pro PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="3c2c0-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [<span data-ttu-id="3c2c0-113">Postupy: Implementace rozdělovače pro statické dělení</span><span class="sxs-lookup"><span data-stu-id="3c2c0-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
