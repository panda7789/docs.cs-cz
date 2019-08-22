---
title: 'Postupy: Použití příkazu ForEach k odebrání položek v BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collection
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 10fa77f6948a10959db5f79c37692eba67d47ecd
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666543"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="acb97-102">Postupy: Použití příkazu ForEach k odebrání položek v BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="acb97-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>

<span data-ttu-id="acb97-103">Kromě pořizování <xref:System.Collections.Concurrent.BlockingCollection%601> položek z <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> a pomocí metody a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> můžete také použít [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([pro každý](../../../visual-basic/language-reference/statements/for-each-next-statement.md) z Visual Basic) k odebrání položek, dokud není přidávání dokončeno a kolekce je prázdná.</span><span class="sxs-lookup"><span data-stu-id="acb97-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="acb97-104">To se označuje jako *obdobná výčet* nebo použití *výčtu* , protože na rozdíl od typické `foreach` (`For Each`) smyčky tento enumerátor upraví zdrojovou kolekci odebráním položek.</span><span class="sxs-lookup"><span data-stu-id="acb97-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>

## <a name="example"></a><span data-ttu-id="acb97-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="acb97-105">Example</span></span>

<span data-ttu-id="acb97-106">Následující příklad ukazuje, jak odebrat všechny položky v a <xref:System.Collections.Concurrent.BlockingCollection%601> `foreach` pomocí smyčky (`For Each`).</span><span class="sxs-lookup"><span data-stu-id="acb97-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

<span data-ttu-id="acb97-107">V tomto příkladu <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> se `foreach` používá smyčka s metodou ve vybírající vlákně, což způsobí, že každá položka bude z kolekce odebrána, protože je vytvořena její výčet.</span><span class="sxs-lookup"><span data-stu-id="acb97-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="acb97-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>omezí maximální počet položek, které jsou v kolekci v každém okamžiku.</span><span class="sxs-lookup"><span data-stu-id="acb97-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="acb97-109">Výčet kolekce tímto způsobem blokuje příjemce vlákna, pokud nejsou k dispozici žádné položky nebo pokud je kolekce prázdná.</span><span class="sxs-lookup"><span data-stu-id="acb97-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="acb97-110">V tomto příkladu blokování není obavy, protože vlákno producenta přidává položky rychleji, než mohou být spotřebovány.</span><span class="sxs-lookup"><span data-stu-id="acb97-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>

<span data-ttu-id="acb97-111">Není zaručeno, že se položky zobrazí ve stejném pořadí, ve kterém jsou přidány vlákny producenta.</span><span class="sxs-lookup"><span data-stu-id="acb97-111">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>

<span data-ttu-id="acb97-112">Chcete-li vytvořit výčet kolekce bez změny, stačí `foreach` použít`For Each`() bez <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="acb97-112">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="acb97-113">Je však důležité pochopit, že tento druh výčtu představuje snímek kolekce v přesném časovém bodě.</span><span class="sxs-lookup"><span data-stu-id="acb97-113">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="acb97-114">Pokud jiné vlákna přidávají nebo odebírají položky souběžně při provádění smyčky, pak smyčka nemusí představovat skutečný stav kolekce.</span><span class="sxs-lookup"><span data-stu-id="acb97-114">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="acb97-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acb97-115">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="acb97-116">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="acb97-116">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)
