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
ms.openlocfilehash: f7cb18157122d8bc053f34b21f623f3ab1e14305
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a>Postupy: Vytvoření fondu objektů pomocí ConcurrentBag
Tento příklad ukazuje způsob použití kontejner souběžných implementovat fondu objektů. Objekt fondy může zlepšit výkon aplikací v situacích, kdy budete potřebovat více instancí třídy a třídy je náročné vytvořit nebo odstranit. Pokud program klient požádá o nový objekt, fond objektů napřed pokusí zadejte jeden, který byl vytvořen a vrátí do fondu. Pokud není k dispozici, pouze nový objekt, který vytvoří se.  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601>slouží k ukládání objektů, protože podporuje rychlé vložení a odebrání, zejména v případě, že je ve stejném vlákně, v jak přidávání a odebírání položek. V tomto příkladu může další rozšířen má být sestaven kolem <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, která implementuje strukturu dat kontejner objektů a dat, stejně jako <xref:System.Collections.Concurrent.ConcurrentQueue%601> a <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a>Viz také  
 [Kolekce bezpečné pro přístup z více vláken](../../../../docs/standard/collections/thread-safe/index.md)
