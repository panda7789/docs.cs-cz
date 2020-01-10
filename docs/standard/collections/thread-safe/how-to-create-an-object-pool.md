---
title: 'Postupy: Vytvoření fondu objektů pomocí ConcurrentBag'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
ms.openlocfilehash: 888521eb5c3c3169c4b39a26e82fef2e35c286d9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711269"
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="ef494-102">Postupy: Vytvoření fondu objektů pomocí ConcurrentBag</span><span class="sxs-lookup"><span data-stu-id="ef494-102">How to: Create an Object Pool by Using a ConcurrentBag</span></span>
<span data-ttu-id="ef494-103">Tento příklad ukazuje, jak použít souběžný kontejner k implementaci fondu objektů.</span><span class="sxs-lookup"><span data-stu-id="ef494-103">This example shows how to use a concurrent bag to implement an object pool.</span></span> <span data-ttu-id="ef494-104">Fondy objektů můžou zlepšit výkon aplikace v situacích, kdy požadujete více instancí třídy a že je třída nenáročná na vytvoření nebo zničení.</span><span class="sxs-lookup"><span data-stu-id="ef494-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="ef494-105">Když klientský program požádá o nový objekt, fond objektů se nejprve pokusí zadat, který již byl vytvořen a vrácen do fondu.</span><span class="sxs-lookup"><span data-stu-id="ef494-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="ef494-106">Pokud není k dispozici žádný, je vytvořen nový objekt.</span><span class="sxs-lookup"><span data-stu-id="ef494-106">If none is available, only then is a new object created.</span></span>  
  
 <span data-ttu-id="ef494-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> slouží k uložení objektů, protože podporuje rychlé vkládání a odebírání, zejména v případě, že stejné vlákno přidává i odebírá položky.</span><span class="sxs-lookup"><span data-stu-id="ef494-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="ef494-108">Tento příklad může být dále rozšířen tak, aby byl sestaven kolem <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, které implementuje struktura dat balíčku, jak <xref:System.Collections.Concurrent.ConcurrentQueue%601> a <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="ef494-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef494-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef494-109">Example</span></span>  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="ef494-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef494-110">See also</span></span>

- [<span data-ttu-id="ef494-111">Kolekce se zabezpečenými vlákny</span><span class="sxs-lookup"><span data-stu-id="ef494-111">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
