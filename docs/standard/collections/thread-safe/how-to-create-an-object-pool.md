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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711269"
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="c9aee-102">Postupy: Vytvoření fondu objektů pomocí ConcurrentBag</span><span class="sxs-lookup"><span data-stu-id="c9aee-102">How to: Create an Object Pool by Using a ConcurrentBag</span></span>
<span data-ttu-id="c9aee-103">Tento příklad ukazuje, jak použít souběžný vak k implementaci fondu objektů.</span><span class="sxs-lookup"><span data-stu-id="c9aee-103">This example shows how to use a concurrent bag to implement an object pool.</span></span> <span data-ttu-id="c9aee-104">Fondy objektů mohou zlepšit výkon aplikace v situacích, kdy požadujete více instancí třídy a třída je nákladné vytvořit nebo zničit.</span><span class="sxs-lookup"><span data-stu-id="c9aee-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="c9aee-105">Když klientský program požaduje nový objekt, fond objektů se nejprve pokusí poskytnout objekt, který již byl vytvořen a vrácen do fondu.</span><span class="sxs-lookup"><span data-stu-id="c9aee-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="c9aee-106">Pokud žádný není k dispozici, pouze potom je vytvořen nový objekt.</span><span class="sxs-lookup"><span data-stu-id="c9aee-106">If none is available, only then is a new object created.</span></span>  
  
 <span data-ttu-id="c9aee-107"><xref:System.Collections.Concurrent.ConcurrentBag%601>Slouží k ukládání objektů, protože podporuje rychlé vkládání a odebírání, zejména v případě, že stejné vlákno přidává i odebírá položky.</span><span class="sxs-lookup"><span data-stu-id="c9aee-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="c9aee-108">Tento příklad by mohl být dále <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>rozšířen tak, aby byl postaven <xref:System.Collections.Concurrent.ConcurrentQueue%601> kolem <xref:System.Collections.Concurrent.ConcurrentStack%601>, který implementuje datová struktura vaku, stejně jako do a .</span><span class="sxs-lookup"><span data-stu-id="c9aee-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9aee-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9aee-109">Example</span></span>  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="c9aee-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9aee-110">See also</span></span>

- [<span data-ttu-id="c9aee-111">Kolekce se zabezpečenými vlákny</span><span class="sxs-lookup"><span data-stu-id="c9aee-111">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
