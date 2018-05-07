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
ms.openlocfilehash: 9313f1064534702fdc2d239eb7f0f69a470329e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a>Postupy: Použití polí blokujících kolekcí v datovém kanálu
Následující příklad ukazuje způsob použití pole <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objekty s statické metody, jako <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> implementovat data rychlé a flexibilní přenos mezi součástmi.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje základní kanálu implementace, ve kterém je každý objekt souběžně bere data ze vstupní kolekce, transformuje je a předání do kolekce výstup.  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
