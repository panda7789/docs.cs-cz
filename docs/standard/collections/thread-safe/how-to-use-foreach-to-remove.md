---
title: 'Postupy: Použití příkazu ForEach k odebrání položek v kolekci BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collectoin
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44b71ed726af585259b015c608e49d8c81e4e22a
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45512852"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="d0d5c-102">Postupy: Použití příkazu ForEach k odebrání položek v kolekci BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="d0d5c-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>
<span data-ttu-id="d0d5c-103">Kromě odebírání položek z <xref:System.Collections.Concurrent.BlockingCollection%601> pomocí <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metodu, můžete použít také [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([pro každou](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) v jazyce Visual Basic) k odebrání položek, dokud se přidání je dokončení a kolekce je prázdná.</span><span class="sxs-lookup"><span data-stu-id="d0d5c-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="d0d5c-104">Tento postup se nazývá *mutace výčet* nebo *využívání výčet* proto, že na rozdíl od typické `foreach` (`For Each`) smyčky, výčet upraví tak, že odeberete zdrojové kolekce položky.</span><span class="sxs-lookup"><span data-stu-id="d0d5c-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0d5c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0d5c-105">Example</span></span>  
 <span data-ttu-id="d0d5c-106">Následující příklad ukazuje, jak odebrat všechny položky v <xref:System.Collections.Concurrent.BlockingCollection%601> pomocí `foreach` (`For Each`) smyčky.</span><span class="sxs-lookup"><span data-stu-id="d0d5c-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 <span data-ttu-id="d0d5c-107">Tento příklad používá `foreach` smyčky s <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> metoda v konzumním vlákně, což způsobí, že jednotlivé položky na odebrat z kolekce, protože je uveden.</span><span class="sxs-lookup"><span data-stu-id="d0d5c-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="d0d5c-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> Omezí maximální počet položek, které jsou v kolekci v každém okamžiku.</span><span class="sxs-lookup"><span data-stu-id="d0d5c-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="d0d5c-109">Vytváření výčtu kolekce tímto způsobem blokuje vlákno příjemce, pokud žádné položky jsou k dispozici nebo pokud kolekce je prázdná.</span><span class="sxs-lookup"><span data-stu-id="d0d5c-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="d0d5c-110">V tomto příkladu blokuje není důležité, protože vlákno výrobce přidá položky rychleji, než mohou být využívány.</span><span class="sxs-lookup"><span data-stu-id="d0d5c-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>  
  
 <span data-ttu-id="d0d5c-111">Není zaručeno, že položky jsou uvedené ve stejném pořadí, ve které se přidají vlákny výrobce.</span><span class="sxs-lookup"><span data-stu-id="d0d5c-111">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>  
  
 <span data-ttu-id="d0d5c-112">K vytvoření výčtu kolekce bez její změny, stačí použít `foreach` (`For Each`) bez <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d0d5c-112">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="d0d5c-113">Je důležité pochopit, že tento druh výčtu představuje snímek kolekce na konkrétním místě v čase.</span><span class="sxs-lookup"><span data-stu-id="d0d5c-113">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="d0d5c-114">Pokud jiná vlákna jsou přidávání a odebírání položek současně, zatímco spouštíte smyčky, nemusí představovat smyčky skutečný stav kolekce.</span><span class="sxs-lookup"><span data-stu-id="d0d5c-114">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0d5c-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0d5c-115">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- [<span data-ttu-id="d0d5c-116">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="d0d5c-116">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)
