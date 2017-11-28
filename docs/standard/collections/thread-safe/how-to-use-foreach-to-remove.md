---
title: "Postupy: Použití příkazu ForEach k odebrání položek v kolekci BlockingCollection"
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
helpviewer_keywords: thread-safe collections, how to enumerate blocking collectoin
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7683e295bd1d898e112a754b06993dabf4483871
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="96aef-102">Postupy: Použití příkazu ForEach k odebrání položek v kolekci BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="96aef-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>
<span data-ttu-id="96aef-103">Kromě přijímání položek z <xref:System.Collections.Concurrent.BlockingCollection%601> pomocí <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metodu, můžete také použít [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([pro každou](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) v jazyce Visual Basic) odebrat položky, dokud nebude přidání byla dokončena a kolekce je prázdná.</span><span class="sxs-lookup"><span data-stu-id="96aef-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="96aef-104">Tento postup se nazývá *mutace – výčet* nebo *využívání – výčet* proto, že na rozdíl od typické `foreach` (`For Each`) ve smyčce, výčet upraví zdrojové kolekci odebráním položky.</span><span class="sxs-lookup"><span data-stu-id="96aef-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96aef-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="96aef-105">Example</span></span>  
 <span data-ttu-id="96aef-106">Následující příklad ukazuje, jak odebrat všechny položky v <xref:System.Collections.Concurrent.BlockingCollection%601> pomocí `foreach` (`For Each`) smyčky.</span><span class="sxs-lookup"><span data-stu-id="96aef-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 <span data-ttu-id="96aef-107">Tento příklad používá `foreach` cykly s <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> metoda ve vláknu, což způsobí, že každá položka má být odebrán z kolekce, jak je uvedené.</span><span class="sxs-lookup"><span data-stu-id="96aef-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="96aef-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>omezuje maximální počet položek, které jsou v kolekci kdykoli.</span><span class="sxs-lookup"><span data-stu-id="96aef-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="96aef-109">Procházení kolekce tímto způsobem blokuje vlákno příjemce, pokud žádné položky jsou k dispozici nebo pokud je kolekce prázdná.</span><span class="sxs-lookup"><span data-stu-id="96aef-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="96aef-110">V tomto příkladu blokování není důležité, protože vlákno výrobce přidává položky rychleji, než mohou být využívány.</span><span class="sxs-lookup"><span data-stu-id="96aef-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>  
  
 <span data-ttu-id="96aef-111">Není zaručeno, že položky jsou uvedené ve stejném pořadí, ve kterém budou přidány vlákny výrobce.</span><span class="sxs-lookup"><span data-stu-id="96aef-111">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>  
  
 <span data-ttu-id="96aef-112">Výčet kolekce beze změny ji, použijte `foreach` (`For Each`) bez <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="96aef-112">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="96aef-113">Je ale důležité si uvědomit, že tento druh výčtu představuje snímek kolekce na přesné bodu v čase.</span><span class="sxs-lookup"><span data-stu-id="96aef-113">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="96aef-114">Pokud jiná vlákna se přidávání nebo odebírání položek současně, zatímco jsou prováděny smyčky, nemusí smyčky reprezentovat skutečný stav kolekce.</span><span class="sxs-lookup"><span data-stu-id="96aef-114">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96aef-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="96aef-115">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="96aef-116">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="96aef-116">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)
