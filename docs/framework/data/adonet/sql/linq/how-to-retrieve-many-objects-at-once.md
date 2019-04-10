---
title: 'Postupy: Načtení mnoha objektů najednou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 18aff4d8-bde8-461b-9960-ccabb24e9d22
ms.openlocfilehash: dd53c2fd16a82ce0f69a33e0b7d7ffef7815b91b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220523"
---
# <a name="how-to-retrieve-many-objects-at-once"></a>Postupy: Načtení mnoha objektů najednou
Mnoho objektů v jednom dotazu můžete načíst pomocí <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.  
  
## <a name="example"></a>Příklad  
 Následující kód používá <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> metody k získání obou `Customer` a `Order` objekty.  
  
 [!code-csharp[DLinqQueryConcepts#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#9)]
 [!code-vb[DLinqQueryConcepts#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#9)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
