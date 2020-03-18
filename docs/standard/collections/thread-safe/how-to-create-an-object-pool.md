---
title: 'Postupy: Vytvoření fondu objektů pomocí ConcurrentBag'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
ms.openlocfilehash: 888521eb5c3c3169c4b39a26e82fef2e35c286d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711269"
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a>Postupy: Vytvoření fondu objektů pomocí ConcurrentBag
Tento příklad ukazuje, jak použít souběžný vak k implementaci fondu objektů. Fondy objektů mohou zlepšit výkon aplikace v situacích, kdy požadujete více instancí třídy a třída je nákladné vytvořit nebo zničit. Když klientský program požaduje nový objekt, fond objektů se nejprve pokusí poskytnout objekt, který již byl vytvořen a vrácen do fondu. Pokud žádný není k dispozici, pouze potom je vytvořen nový objekt.  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601>Slouží k ukládání objektů, protože podporuje rychlé vkládání a odebírání, zejména v případě, že stejné vlákno přidává i odebírá položky. Tento příklad by mohl být dále <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>rozšířen tak, aby byl postaven <xref:System.Collections.Concurrent.ConcurrentQueue%601> kolem <xref:System.Collections.Concurrent.ConcurrentStack%601>, který implementuje datová struktura vaku, stejně jako do a .  
  
## <a name="example"></a>Příklad  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a>Viz také

- [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
