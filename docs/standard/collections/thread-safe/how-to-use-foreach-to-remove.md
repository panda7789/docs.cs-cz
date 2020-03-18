---
title: 'Postupy: Použití příkazu ForEach k odebrání položek v kolekci BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collection
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
ms.openlocfilehash: f9a858dea74be63634f887c4204aefa8ac338ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711230"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="3cfd1-102">Postupy: Použití příkazu ForEach k odebrání položek v kolekci BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="3cfd1-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>

<span data-ttu-id="3cfd1-103">Kromě přijímání položek z <xref:System.Collections.Concurrent.BlockingCollection%601> pomocí <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> metody <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> a můžete také použít [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) v jazyce Visual Basic) k odebrání položek, dokud není přidání dokončeno a kolekce je prázdná.</span><span class="sxs-lookup"><span data-stu-id="3cfd1-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="3cfd1-104">To se nazývá *mutující výčt* nebo *spotřebovává výčtu,* `foreach` protože`For Each`na rozdíl od typické ( ) smyčky tento čítač výčtu upravuje zdrojové kolekce odebráním položek.</span><span class="sxs-lookup"><span data-stu-id="3cfd1-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>

## <a name="example"></a><span data-ttu-id="3cfd1-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="3cfd1-105">Example</span></span>

<span data-ttu-id="3cfd1-106">Následující příklad ukazuje, jak odebrat <xref:System.Collections.Concurrent.BlockingCollection%601> všechny položky v a pomocí `foreach` smyčky (`For Each`).</span><span class="sxs-lookup"><span data-stu-id="3cfd1-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

<span data-ttu-id="3cfd1-107">Tento příklad `foreach` používá smyčku s <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> metodou v náročnévlákno, což způsobí, že každá položka má být odebrána z kolekce, jak je uveden.</span><span class="sxs-lookup"><span data-stu-id="3cfd1-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="3cfd1-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>omezuje maximální počet položek, které jsou v kolekci kdykoli.</span><span class="sxs-lookup"><span data-stu-id="3cfd1-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="3cfd1-109">Výčet kolekce tímto způsobem blokuje vlákno příjemce, pokud nejsou k dispozici žádné položky nebo pokud je kolekce prázdná.</span><span class="sxs-lookup"><span data-stu-id="3cfd1-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="3cfd1-110">V tomto příkladu blokování není problém, protože vlákno výrobce přidá položky rychleji, než mohou být spotřebovány.</span><span class="sxs-lookup"><span data-stu-id="3cfd1-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>

<span data-ttu-id="3cfd1-111">Neexistuje žádná záruka, že položky jsou uvedeny ve stejném pořadí, ve kterém jsou přidány podprocesy výrobce.</span><span class="sxs-lookup"><span data-stu-id="3cfd1-111">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>

<span data-ttu-id="3cfd1-112">Chcete-li vytvořit výčet kolekce bez úpravy, stačí použít `foreach` (`For Each`) bez <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3cfd1-112">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="3cfd1-113">Je však důležité si uvědomit, že tento druh výčtu představuje snímek kolekce v přesném okamžiku v čase.</span><span class="sxs-lookup"><span data-stu-id="3cfd1-113">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="3cfd1-114">Pokud ostatní vlákna přidávají nebo odebírají položky souběžně při provádění smyčky, smyčka nemusí představovat skutečný stav kolekce.</span><span class="sxs-lookup"><span data-stu-id="3cfd1-114">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="3cfd1-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3cfd1-115">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="3cfd1-116">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="3cfd1-116">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)
