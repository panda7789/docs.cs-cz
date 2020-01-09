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
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a>Postupy: Použití polí blokujících kolekcí v datovém kanálu
Následující příklad ukazuje, jak použít pole objektů <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> se statickými metodami, jako jsou <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> k implementaci rychlého a flexibilního přenosu dat mezi komponentami.  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje základní implementaci kanálu, ve kterém každý objekt souběžně přebírá data ze vstupní kolekce, transformuje je a předává do výstupní kolekce.  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
