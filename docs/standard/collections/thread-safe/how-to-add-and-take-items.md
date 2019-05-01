---
title: 'Postupy: Přidávání a odebírání jednotlivých položek v BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e24c6b5aa02e8bc7ca4bcbf2c69bffd06216962
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054286"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a><span data-ttu-id="d749b-102">Postupy: Přidávání a odebírání jednotlivých položek v BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="d749b-102">How to: Add and Take Items Individually from a BlockingCollection</span></span>
<span data-ttu-id="d749b-103">Tento příklad ukazuje, jak přidávat a odebírat položky z <xref:System.Collections.Concurrent.BlockingCollection%601> blokování a neblokující způsobem.</span><span class="sxs-lookup"><span data-stu-id="d749b-103">This example shows how to add and remove items from a <xref:System.Collections.Concurrent.BlockingCollection%601> in both a blocking and a non-blocking manner.</span></span> <span data-ttu-id="d749b-104">Další informace o <xref:System.Collections.Concurrent.BlockingCollection%601>, naleznete v tématu [BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d749b-104">For more information on <xref:System.Collections.Concurrent.BlockingCollection%601>, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
 <span data-ttu-id="d749b-105">Příklad toho, jak vytvořit výčet <xref:System.Collections.Concurrent.BlockingCollection%601> dokud je prázdný a nebudou přidány žádné další prvky, naleznete v tématu [jak: Použití příkazu ForEach k odebrání položek v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span><span class="sxs-lookup"><span data-stu-id="d749b-105">For an example of how to enumerate a <xref:System.Collections.Concurrent.BlockingCollection%601> until it is empty and no more elements will be added, see [How to: Use ForEach to Remove Items in a BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="d749b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d749b-106">Example</span></span>  
 <span data-ttu-id="d749b-107">Tento první příklad ukazuje, jak přidat a převzít položky tak, aby operace budou blokovat, pokud kolekce je buď dočasně prázdný (když se vezme) nebo na maximální kapacita (při přidávání), nebo pokud má zadaný časový limit vypršel.</span><span class="sxs-lookup"><span data-stu-id="d749b-107">This first example shows how to add and take items so that the operations will block if the collection is either temporarily empty (when taking) or at maximum capacity (when adding), or if a specified timeout period has elapsed.</span></span> <span data-ttu-id="d749b-108">Všimněte si, že blokování maximální kapacity je povolená jenom při BlockingCollection byl vytvořen s maximální kapacita určená v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d749b-108">Note that blocking on maximum capacity is only enabled when the BlockingCollection has been created with a maximum capacity specified in the constructor.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="d749b-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d749b-109">Example</span></span>  
 <span data-ttu-id="d749b-110">Tento druhý příklad ukazuje, jak přidat a pořiďte položek nebude blokovat operace.</span><span class="sxs-lookup"><span data-stu-id="d749b-110">This second example shows how to add and take items so that the operations will not block.</span></span> <span data-ttu-id="d749b-111">Pokud není k dispozici žádná položka, bylo dosaženo maximální kapacity na ohraničené kolekce nebo vypršel časový limit, pak bude <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> nebo <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operace vrátí hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="d749b-111">If no item is present, maximum capacity on a bounded collection has been reached, or the timeout period has elapsed, then the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operation returns false.</span></span> <span data-ttu-id="d749b-112">To umožňuje vláknu provádět další užitečné operace nějakou dobu a opakujte akci později k načtení nové položky, nebo znovu zkusíte přidat stejnou položku, kterou nebylo možné přidat dříve.</span><span class="sxs-lookup"><span data-stu-id="d749b-112">This allows the thread to do some other useful work for a while and then try again later to either retrieve a new item, or try to add the same item that could not be added previously.</span></span> <span data-ttu-id="d749b-113">Program také ukazuje, jak implementovat při přístupu ke zrušení <xref:System.Collections.Concurrent.BlockingCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="d749b-113">The program also demonstrates how to implement cancellation when accessing a <xref:System.Collections.Concurrent.BlockingCollection%601>.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="d749b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d749b-114">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="d749b-115">BlockingCollection – přehled</span><span class="sxs-lookup"><span data-stu-id="d749b-115">BlockingCollection Overview</span></span>](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
