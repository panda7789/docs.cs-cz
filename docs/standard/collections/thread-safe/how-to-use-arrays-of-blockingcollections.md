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
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a>Postupy: Použití polí blokujících kolekcí v datovém kanálu
Následující příklad ukazuje způsob použití pole <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objekty s statické metody, jako <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> implementovat data rychlé a flexibilní přenos mezi součástmi.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje základní kanálu implementace, ve kterém je každý objekt souběžně bere data ze vstupní kolekce, transformuje je a předání do kolekce výstup.  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [Kolekce bezpečné pro přístup z více vláken](../../../../docs/standard/collections/thread-safe/index.md)
