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
ms.openlocfilehash: 3f4270d2ec71421bad8974a3e5cd8f1d65db3b74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711295"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a><span data-ttu-id="67372-102">Postupy: Přidávání odebírání jednotlivých položek v BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="67372-102">How to: Add and Take Items Individually from a BlockingCollection</span></span>
<span data-ttu-id="67372-103">Tento příklad ukazuje, jak přidat <xref:System.Collections.Concurrent.BlockingCollection%601> a odebrat položky z blokování a neblokující způsobem.</span><span class="sxs-lookup"><span data-stu-id="67372-103">This example shows how to add and remove items from a <xref:System.Collections.Concurrent.BlockingCollection%601> in both a blocking and a non-blocking manner.</span></span> <span data-ttu-id="67372-104">Další informace <xref:System.Collections.Concurrent.BlockingCollection%601>naleznete v tématu [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="67372-104">For more information on <xref:System.Collections.Concurrent.BlockingCollection%601>, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
 <span data-ttu-id="67372-105">Příklad, jak <xref:System.Collections.Concurrent.BlockingCollection%601> výčet, dokud není prázdný a žádné další prvky budou přidány, naleznete v [tématu: Použití ForEach odebrat položky v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span><span class="sxs-lookup"><span data-stu-id="67372-105">For an example of how to enumerate a <xref:System.Collections.Concurrent.BlockingCollection%601> until it is empty and no more elements will be added, see [How to: Use ForEach to Remove Items in a BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="67372-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="67372-106">Example</span></span>  
 <span data-ttu-id="67372-107">Tento první příklad ukazuje, jak přidat a přijmout položky tak, aby operace bude blokovat, pokud kolekce je buď dočasně prázdný (při převzetí) nebo na maximální kapacitu (při přidávání), nebo pokud uplynula zadaná doba časového limitu.</span><span class="sxs-lookup"><span data-stu-id="67372-107">This first example shows how to add and take items so that the operations will block if the collection is either temporarily empty (when taking) or at maximum capacity (when adding), or if a specified timeout period has elapsed.</span></span> <span data-ttu-id="67372-108">Všimněte si, že blokování na maximální kapacitu je povoleno pouze v případě, že BlockingCollection byla vytvořena s maximální kapacitou zadanou v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="67372-108">Note that blocking on maximum capacity is only enabled when the BlockingCollection has been created with a maximum capacity specified in the constructor.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="67372-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="67372-109">Example</span></span>  
 <span data-ttu-id="67372-110">Tento druhý příklad ukazuje, jak přidat a přijmout položky tak, aby operace nebudou blokovat.</span><span class="sxs-lookup"><span data-stu-id="67372-110">This second example shows how to add and take items so that the operations will not block.</span></span> <span data-ttu-id="67372-111">Pokud není k dispozici žádná položka, bylo dosaženo maximální kapacity v ohraničené kolekci <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> nebo uplynulčasový limit, vrátí operace nebo false.</span><span class="sxs-lookup"><span data-stu-id="67372-111">If no item is present, maximum capacity on a bounded collection has been reached, or the timeout period has elapsed, then the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operation returns false.</span></span> <span data-ttu-id="67372-112">To umožňuje vlákno provést některé další užitečné práce na chvíli a zkuste to znovu později buď načíst novou položku, nebo zkuste přidat stejnou položku, která nemohla být přidána dříve.</span><span class="sxs-lookup"><span data-stu-id="67372-112">This allows the thread to do some other useful work for a while and then try again later to either retrieve a new item, or try to add the same item that could not be added previously.</span></span> <span data-ttu-id="67372-113">Program také ukazuje, jak implementovat zrušení <xref:System.Collections.Concurrent.BlockingCollection%601>při přístupu k .</span><span class="sxs-lookup"><span data-stu-id="67372-113">The program also demonstrates how to implement cancellation when accessing a <xref:System.Collections.Concurrent.BlockingCollection%601>.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="67372-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="67372-114">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="67372-115">BlockingCollection – přehled</span><span class="sxs-lookup"><span data-stu-id="67372-115">BlockingCollection Overview</span></span>](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
