---
title: "Postupy: Přidávání odebírání jednotlivých položek v BlockingCollection"
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
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c19e78ca05b339898a27a1e5f98412224586aae9
ms.sourcegitcommit: c3ebb11a66e85a465c9ba2c42592222630b7ff9e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a><span data-ttu-id="6d60c-102">Postupy: Přidávání odebírání jednotlivých položek v BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="6d60c-102">How to: Add and Take Items Individually from a BlockingCollection</span></span>
<span data-ttu-id="6d60c-103">Tento příklad ukazuje, jak k přidání a odebrání položek z <xref:System.Collections.Concurrent.BlockingCollection%601> blokování a neblokující způsobem.</span><span class="sxs-lookup"><span data-stu-id="6d60c-103">This example shows how to add and remove items from a <xref:System.Collections.Concurrent.BlockingCollection%601> in both a blocking and a non-blocking manner.</span></span> <span data-ttu-id="6d60c-104">Další informace o <xref:System.Collections.Concurrent.BlockingCollection%601>, najdete v části [BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6d60c-104">For more information on <xref:System.Collections.Concurrent.BlockingCollection%601>, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
 <span data-ttu-id="6d60c-105">Příklad toho, jak vytvořit výčet <xref:System.Collections.Concurrent.BlockingCollection%601> dokud je prázdný, a budou přidány žádné další prvky, najdete v části [postupy: použití příkazu ForEach k odebrání položek v kolekci BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span><span class="sxs-lookup"><span data-stu-id="6d60c-105">For an example of how to enumerate a <xref:System.Collections.Concurrent.BlockingCollection%601> until it is empty and no more elements will be added, see [How to: Use ForEach to Remove Items in a BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="6d60c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d60c-106">Example</span></span>  
 <span data-ttu-id="6d60c-107">Tento první příklad ukazuje, jak přidat a převzít položky tak, aby operace zablokuje, pokud kolekce je buď dočasně prázdný (když se vezme) nebo na maximální kapacity (při přidávání), nebo pokud dojde k uplynutí zadaného časového limitu.</span><span class="sxs-lookup"><span data-stu-id="6d60c-107">This first example shows how to add and take items so that the operations will block if the collection is either temporarily empty (when taking) or at maximum capacity (when adding), or if a specified timeout period has elapsed.</span></span> <span data-ttu-id="6d60c-108">Všimněte si, že blokování na maximální kapacitě je povoleno pouze pokud BlockingCollection byl vytvořen s maximální kapacita určená v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="6d60c-108">Note that blocking on maximum capacity is only enabled when the BlockingCollection has been created with a maximum capacity specified in the constructor.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="6d60c-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d60c-109">Example</span></span>  
 <span data-ttu-id="6d60c-110">Tento druhý příklad ukazuje, jak přidat a převzít položky tak, aby operace se nebude blokovat.</span><span class="sxs-lookup"><span data-stu-id="6d60c-110">This second example shows how to add and take items so that the operations will not block.</span></span> <span data-ttu-id="6d60c-111">Pokud je k dispozici žádné položky, bylo dosaženo maximální kapacity u ohraničené kolekce nebo uplynutí časového limitu, pak se <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> nebo <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operace vrací hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="6d60c-111">If no item is present, maximum capacity on a bounded collection has been reached, or the timeout period has elapsed, then the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operation returns false.</span></span> <span data-ttu-id="6d60c-112">To umožňuje vláknu provádět některé další užitečné činnosti na chvíli a opakujte akci později buď načíst nové položky, nebo zkuste přidat stejnou položku, kterou nebylo možné přidat dříve.</span><span class="sxs-lookup"><span data-stu-id="6d60c-112">This allows the thread to do some other useful work for a while and then try again later to either retrieve a new item, or try to add the same item that could not be added previously.</span></span> <span data-ttu-id="6d60c-113">Program také ukazuje, jak implementovat zrušení při přístupu k <xref:System.Collections.Concurrent.BlockingCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="6d60c-113">The program also demonstrates how to implement cancellation when accessing a <xref:System.Collections.Concurrent.BlockingCollection%601>.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="6d60c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d60c-114">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="6d60c-115">BlockingCollection – přehled</span><span class="sxs-lookup"><span data-stu-id="6d60c-115">BlockingCollection Overview</span></span>](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
