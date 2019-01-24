---
title: 'Postupy: Použití polí blokujících kolekcí v kanálu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4667d78fdf91a3e62c22d88c7cbe9effaae57d5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627197"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="96785-102">Postupy: Použití polí blokujících kolekcí v kanálu</span><span class="sxs-lookup"><span data-stu-id="96785-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>
<span data-ttu-id="96785-103">Následující příklad ukazuje způsob použití pole <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objekty se statickými metodami, jako <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> implementovat rychlé a flexibilní přenos dat mezi součástmi.</span><span class="sxs-lookup"><span data-stu-id="96785-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96785-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="96785-104">Example</span></span>  
 <span data-ttu-id="96785-105">Následující příklad ukazuje implementaci základní kanál, ve kterém každý objekt současně trvá data ze vstupní kolekce, jejich transformace a předá se výstup kolekce.</span><span class="sxs-lookup"><span data-stu-id="96785-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a><span data-ttu-id="96785-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96785-106">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="96785-107">Kolekce se zabezpečenými vlákny</span><span class="sxs-lookup"><span data-stu-id="96785-107">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
