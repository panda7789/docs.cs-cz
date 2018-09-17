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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bc0c6bebbab6e84c165f41300a4cb16c8746a07
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45747256"
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="16568-102">Postupy: Vytvoření fondu objektů pomocí ConcurrentBag</span><span class="sxs-lookup"><span data-stu-id="16568-102">How to: Create an Object Pool by Using a ConcurrentBag</span></span>
<span data-ttu-id="16568-103">Tento příklad ukazuje způsob používání souběžného kontejneru za implementace fondu objektů.</span><span class="sxs-lookup"><span data-stu-id="16568-103">This example shows how to use a concurrent bag to implement an object pool.</span></span> <span data-ttu-id="16568-104">Objekt fondy může zlepšit výkon aplikace v situacích, kde budete potřebovat více instancí třídy a třídy je náročné vytvořit nebo odstranit.</span><span class="sxs-lookup"><span data-stu-id="16568-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="16568-105">Když klientský program požádá o objekt, fondu objektů se nejprve pokusí neposkytne, které již byly vytvořeny a vrácen do fondu.</span><span class="sxs-lookup"><span data-stu-id="16568-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="16568-106">Pokud není k dispozici, pouze je nový objekt vytvoří.</span><span class="sxs-lookup"><span data-stu-id="16568-106">If none is available, only then is a new object created.</span></span>  
  
 <span data-ttu-id="16568-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> slouží k ukládání objektů, protože umožňuje rychlé vkládání a odstranění, zejména v případě, že je ve stejném vlákně je jak přidávání a odebírání položek.</span><span class="sxs-lookup"><span data-stu-id="16568-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="16568-108">V tomto příkladu může dále rozšířit má být sestaven kolem <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, který implementuje kontejner objektů a dat datová struktura, stejně jako <xref:System.Collections.Concurrent.ConcurrentQueue%601> a <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="16568-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16568-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="16568-109">Example</span></span>  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="16568-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16568-110">See also</span></span>

- [<span data-ttu-id="16568-111">Kolekce se zabezpečenými vlákny</span><span class="sxs-lookup"><span data-stu-id="16568-111">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
