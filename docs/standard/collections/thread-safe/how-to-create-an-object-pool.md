---
title: "Postupy: Vytvoření fondu objektů pomocí ConcurrentBag"
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
helpviewer_keywords: object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 66cde52d7453e149510d0c2e1d63f9e9182e3e99
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="b61f8-102">Postupy: Vytvoření fondu objektů pomocí ConcurrentBag</span><span class="sxs-lookup"><span data-stu-id="b61f8-102">How to: Create an Object Pool by Using a ConcurrentBag</span></span>
<span data-ttu-id="b61f8-103">Tento příklad ukazuje způsob použití kontejner souběžných implementovat fondu objektů.</span><span class="sxs-lookup"><span data-stu-id="b61f8-103">This example shows how to use a concurrent bag to implement an object pool.</span></span> <span data-ttu-id="b61f8-104">Objekt fondy může zlepšit výkon aplikací v situacích, kdy budete potřebovat více instancí třídy a třídy je náročné vytvořit nebo odstranit.</span><span class="sxs-lookup"><span data-stu-id="b61f8-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="b61f8-105">Pokud program klient požádá o nový objekt, fond objektů napřed pokusí zadejte jeden, který byl vytvořen a vrátí do fondu.</span><span class="sxs-lookup"><span data-stu-id="b61f8-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="b61f8-106">Pokud není k dispozici, pouze nový objekt, který vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="b61f8-106">If none is available, only then is a new object created.</span></span>  
  
 <span data-ttu-id="b61f8-107"><xref:System.Collections.Concurrent.ConcurrentBag%601>slouží k ukládání objektů, protože podporuje rychlé vložení a odebrání, zejména v případě, že je ve stejném vlákně, v jak přidávání a odebírání položek.</span><span class="sxs-lookup"><span data-stu-id="b61f8-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="b61f8-108">V tomto příkladu může další rozšířen má být sestaven kolem <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, která implementuje strukturu dat kontejner objektů a dat, stejně jako <xref:System.Collections.Concurrent.ConcurrentQueue%601> a <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="b61f8-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b61f8-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="b61f8-109">Example</span></span>  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="b61f8-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="b61f8-110">See Also</span></span>  
 [<span data-ttu-id="b61f8-111">Kolekce se zabezpečenými vlákny</span><span class="sxs-lookup"><span data-stu-id="b61f8-111">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
