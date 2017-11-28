---
title: "Postupy: Použití polí blokujících kolekcí v datovém kanálu"
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
helpviewer_keywords: thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ab60561372f2c30055aed95ff60599ea80da1eb8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="4e095-102">Postupy: Použití polí blokujících kolekcí v datovém kanálu</span><span class="sxs-lookup"><span data-stu-id="4e095-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>
<span data-ttu-id="4e095-103">Následující příklad ukazuje způsob použití pole <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objekty s statické metody, jako <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> implementovat data rychlé a flexibilní přenos mezi součástmi.</span><span class="sxs-lookup"><span data-stu-id="4e095-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e095-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e095-104">Example</span></span>  
 <span data-ttu-id="4e095-105">Následující příklad ukazuje základní kanálu implementace, ve kterém je každý objekt souběžně bere data ze vstupní kolekce, transformuje je a předání do kolekce výstup.</span><span class="sxs-lookup"><span data-stu-id="4e095-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a><span data-ttu-id="4e095-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e095-106">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="4e095-107">Kolekce bezpečné pro přístup z více vláken</span><span class="sxs-lookup"><span data-stu-id="4e095-107">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
