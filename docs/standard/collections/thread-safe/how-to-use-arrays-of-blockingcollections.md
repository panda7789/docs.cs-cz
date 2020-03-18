---
title: 'Postupy: Použití polí blokujících kolekcí v datovém kanálu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
ms.openlocfilehash: 397c438bacd1cfed1613efef61e9d7266d55ea47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711256"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="25138-102">Postupy: Použití polí blokujících kolekcí v datovém kanálu</span><span class="sxs-lookup"><span data-stu-id="25138-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>
<span data-ttu-id="25138-103">Následující příklad ukazuje, jak používat <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> pole objektů se <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> statickými metodami, jako je například a implementovat rychlý a flexibilní přenos dat mezi součástmi.</span><span class="sxs-lookup"><span data-stu-id="25138-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25138-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="25138-104">Example</span></span>  
 <span data-ttu-id="25138-105">Následující příklad ukazuje základní implementace kanálu, ve kterém každý objekt je současně převzetí dat ze vstupní kolekce, jejich transformaci a předání do výstupní kolekce.</span><span class="sxs-lookup"><span data-stu-id="25138-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a><span data-ttu-id="25138-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="25138-106">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="25138-107">Kolekce se zabezpečenými vlákny</span><span class="sxs-lookup"><span data-stu-id="25138-107">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
