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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711256"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="01d13-102">Postupy: Použití polí blokujících kolekcí v datovém kanálu</span><span class="sxs-lookup"><span data-stu-id="01d13-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>
<span data-ttu-id="01d13-103">Následující příklad ukazuje, jak použít pole objektů <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> se statickými metodami, jako jsou <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> k implementaci rychlého a flexibilního přenosu dat mezi komponentami.</span><span class="sxs-lookup"><span data-stu-id="01d13-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01d13-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="01d13-104">Example</span></span>  
 <span data-ttu-id="01d13-105">Následující příklad znázorňuje základní implementaci kanálu, ve kterém každý objekt souběžně přebírá data ze vstupní kolekce, transformuje je a předává do výstupní kolekce.</span><span class="sxs-lookup"><span data-stu-id="01d13-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a><span data-ttu-id="01d13-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01d13-106">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="01d13-107">Kolekce se zabezpečenými vlákny</span><span class="sxs-lookup"><span data-stu-id="01d13-107">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
