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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2e2e312668a7cf4fe39596ae018adaf62cd850e4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187543"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="d07bd-102">Postupy: Použití polí blokujících kolekcí v datovém kanálu</span><span class="sxs-lookup"><span data-stu-id="d07bd-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>
<span data-ttu-id="d07bd-103">Následující příklad ukazuje způsob použití pole <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objekty se statickými metodami, jako <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> implementovat rychlé a flexibilní přenos dat mezi součástmi.</span><span class="sxs-lookup"><span data-stu-id="d07bd-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d07bd-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d07bd-104">Example</span></span>  
 <span data-ttu-id="d07bd-105">Následující příklad ukazuje implementaci základní kanál, ve kterém každý objekt současně trvá data ze vstupní kolekce, jejich transformace a předá se výstup kolekce.</span><span class="sxs-lookup"><span data-stu-id="d07bd-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a><span data-ttu-id="d07bd-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d07bd-106">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- [<span data-ttu-id="d07bd-107">Kolekce se zabezpečenými vlákny</span><span class="sxs-lookup"><span data-stu-id="d07bd-107">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
