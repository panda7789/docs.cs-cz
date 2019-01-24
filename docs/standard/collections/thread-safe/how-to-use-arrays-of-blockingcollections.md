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
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a>Postupy: Použití polí blokujících kolekcí v kanálu
Následující příklad ukazuje způsob použití pole <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objekty se statickými metodami, jako <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> implementovat rychlé a flexibilní přenos dat mezi součástmi.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje implementaci základní kanál, ve kterém každý objekt současně trvá data ze vstupní kolekce, jejich transformace a předá se výstup kolekce.  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
