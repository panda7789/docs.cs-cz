---
title: 'Postupy: Přidávání odebírání jednotlivých položek v BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
ms.openlocfilehash: f895be4c20a0cccad23e27db3d488355a614cbfc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287884"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a><span data-ttu-id="0c2e9-102">Postupy: Přidávání odebírání jednotlivých položek v BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="0c2e9-102">How to: Add and Take Items Individually from a BlockingCollection</span></span>
<span data-ttu-id="0c2e9-103">Tento příklad ukazuje, jak přidat a odebrat položky z a <xref:System.Collections.Concurrent.BlockingCollection%601> v blokujícím a neblokujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="0c2e9-103">This example shows how to add and remove items from a <xref:System.Collections.Concurrent.BlockingCollection%601> in both a blocking and a non-blocking manner.</span></span> <span data-ttu-id="0c2e9-104">Další informace o <xref:System.Collections.Concurrent.BlockingCollection%601> naleznete v tématu [BlockingCollection – přehled](blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0c2e9-104">For more information on <xref:System.Collections.Concurrent.BlockingCollection%601>, see [BlockingCollection Overview](blockingcollection-overview.md).</span></span>  
  
 <span data-ttu-id="0c2e9-105">Příklad, jak vytvořit výčet a <xref:System.Collections.Concurrent.BlockingCollection%601> dokud není prázdný a další prvky nebudou přidány, naleznete v tématu [How to: use foreach k odebrání položek v blokujícícollection](how-to-use-foreach-to-remove.md).</span><span class="sxs-lookup"><span data-stu-id="0c2e9-105">For an example of how to enumerate a <xref:System.Collections.Concurrent.BlockingCollection%601> until it is empty and no more elements will be added, see [How to: Use ForEach to Remove Items in a BlockingCollection](how-to-use-foreach-to-remove.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="0c2e9-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c2e9-106">Example</span></span>  
 <span data-ttu-id="0c2e9-107">Tento první příklad ukazuje, jak přidat a převzít položky tak, že operace budou blokovat, pokud je kolekce buď dočasně prázdná (při pořízení), nebo s maximální kapacitou (při přidávání), nebo pokud uplynula doba platnosti.</span><span class="sxs-lookup"><span data-stu-id="0c2e9-107">This first example shows how to add and take items so that the operations will block if the collection is either temporarily empty (when taking) or at maximum capacity (when adding), or if a specified timeout period has elapsed.</span></span> <span data-ttu-id="0c2e9-108">Všimněte si, že blokování na maximální kapacitě je povoleno pouze v případě, že je kolekce BlockingCollection vytvořena s maximální kapacitou zadanou v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0c2e9-108">Note that blocking on maximum capacity is only enabled when the BlockingCollection has been created with a maximum capacity specified in the constructor.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="0c2e9-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c2e9-109">Example</span></span>  
 <span data-ttu-id="0c2e9-110">Tento druhý příklad ukazuje, jak přidat a převzít položky, aby operace neblokovaly.</span><span class="sxs-lookup"><span data-stu-id="0c2e9-110">This second example shows how to add and take items so that the operations will not block.</span></span> <span data-ttu-id="0c2e9-111">Pokud není k dispozici žádná položka, byla dosažena maximální kapacita v vázané kolekci nebo vypršel časový limit, <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operace nebo vrátí hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="0c2e9-111">If no item is present, maximum capacity on a bounded collection has been reached, or the timeout period has elapsed, then the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operation returns false.</span></span> <span data-ttu-id="0c2e9-112">To umožňuje, aby vlákno v průběhu chvilku provedlo nějakou další užitečnou práci, a potom to zkuste znovu později načíst novou položku nebo se pokusit přidat stejnou položku, kterou nebylo možné přidat dříve.</span><span class="sxs-lookup"><span data-stu-id="0c2e9-112">This allows the thread to do some other useful work for a while and then try again later to either retrieve a new item, or try to add the same item that could not be added previously.</span></span> <span data-ttu-id="0c2e9-113">Program také ukazuje, jak implementovat zrušení při přístupu k <xref:System.Collections.Concurrent.BlockingCollection%601> .</span><span class="sxs-lookup"><span data-stu-id="0c2e9-113">The program also demonstrates how to implement cancellation when accessing a <xref:System.Collections.Concurrent.BlockingCollection%601>.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="0c2e9-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c2e9-114">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="0c2e9-115">BlockingCollection – přehled</span><span class="sxs-lookup"><span data-stu-id="0c2e9-115">BlockingCollection Overview</span></span>](blockingcollection-overview.md)
