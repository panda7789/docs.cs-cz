---
title: Určení počtu prvků v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: b39b0a1487c9f250e32b13330f2f70b7e3c7c877
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209525"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a>Určení počtu prvků v posloupnosti
Použití <xref:System.Linq.Enumerable.Count%2A> operátor ke zjištění počtu prvků v posloupnosti.  
  
 Běží tento dotaz s ukázkovou databází Northwind vytvoří výstup `91`.  
  
## <a name="example"></a>Příklad  
 Následující příklad vrátí počet `Customers` v databázi.  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vrátí počet produktů v databázi, které dosud nebyly vyřazeny.  
  
 Spuštěním tohoto příkladu s ukázkovou databází Northwind vytvoří výstup `69`.  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Agregační dotazy](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
