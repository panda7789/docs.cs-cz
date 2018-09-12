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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bc0c6bebbab6e84c165f41300a4cb16c8746a07
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44706690"
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a>Postupy: Vytvoření fondu objektů pomocí ConcurrentBag
Tento příklad ukazuje způsob používání souběžného kontejneru za implementace fondu objektů. Objekt fondy může zlepšit výkon aplikace v situacích, kde budete potřebovat více instancí třídy a třídy je náročné vytvořit nebo odstranit. Když klientský program požádá o objekt, fondu objektů se nejprve pokusí neposkytne, které již byly vytvořeny a vrácen do fondu. Pokud není k dispozici, pouze je nový objekt vytvoří.  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601> slouží k ukládání objektů, protože umožňuje rychlé vkládání a odstranění, zejména v případě, že je ve stejném vlákně je jak přidávání a odebírání položek. V tomto příkladu může dále rozšířit má být sestaven kolem <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, který implementuje kontejner objektů a dat datová struktura, stejně jako <xref:System.Collections.Concurrent.ConcurrentQueue%601> a <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a>Viz také:

- [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
