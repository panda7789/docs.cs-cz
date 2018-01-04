---
title: "Postupy: Zrychlení malých smyček"
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
helpviewer_keywords: parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a2e068b38c12d37755bee4c7da8c1ca8e5036c74
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="88bbc-102">Postupy: Zrychlení malých smyček</span><span class="sxs-lookup"><span data-stu-id="88bbc-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="88bbc-103">Když <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> smyčky má malé tělo, jako například může pomaleji než ekvivalentní sekvenční smyčka, proveďte [pro](~/docs/csharp/language-reference/keywords/for.md) smyčky v jazyce C# a [pro](http://msdn.microsoft.com/en-us/c470a263-9b49-4308-8fd6-8592b84a7980) v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="88bbc-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](~/docs/csharp/language-reference/keywords/for.md) loop in C# and the [For](http://msdn.microsoft.com/en-us/c470a263-9b49-4308-8fd6-8592b84a7980) loop in Visual Basic.</span></span> <span data-ttu-id="88bbc-104">Pomalejší výkon je způsobená režie spojená s dělení dat a náklady na vyvolání delegáta na každé iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="88bbc-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="88bbc-105">Chcete-li vyřešit takových scénářů <xref:System.Collections.Concurrent.Partitioner> třída poskytuje <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metoda, která umožňuje poskytovat sekvenční smyčka pro tělo delegáta, tak, aby delegáta je jenom jednou vyvolána na oddíl, namísto jednou za iteraci.</span><span class="sxs-lookup"><span data-stu-id="88bbc-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="88bbc-106">Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="88bbc-106">For more information, see [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="88bbc-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="88bbc-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="88bbc-108">Přístup ukázáno v tomto příkladu je užitečný, když smyčky provede minimální množství práce.</span><span class="sxs-lookup"><span data-stu-id="88bbc-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="88bbc-109">Jakmile je výpočetně náročná, pravděpodobně obdržíte stejnou nebo lepší výkon pomocí <xref:System.Threading.Tasks.Parallel.For%2A> nebo <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky pomocí výchozí dělicí metody.</span><span class="sxs-lookup"><span data-stu-id="88bbc-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88bbc-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="88bbc-110">See Also</span></span>  
 [<span data-ttu-id="88bbc-111">Datový paralelismus</span><span class="sxs-lookup"><span data-stu-id="88bbc-111">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="88bbc-112">Vlastní dělicí metody pro PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="88bbc-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [<span data-ttu-id="88bbc-113">Iterátory</span><span class="sxs-lookup"><span data-stu-id="88bbc-113">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [<span data-ttu-id="88bbc-114">Výrazy lambda v PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="88bbc-114">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
