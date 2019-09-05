---
title: Určení počtu prvků v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 74e24aeb64b0097cba3975e76475034e6bb9544d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247705"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a>Určení počtu prvků v posloupnosti
<xref:System.Linq.Enumerable.Count%2A> Pomocí operátoru můžete spočítat počet prvků v sekvenci.  
  
 Spuštění tohoto dotazu proti ukázkové databázi Northwind vytvoří výstup `91`.  
  
## <a name="example"></a>Příklad  
 Následující příklad spočítá počet `Customers` v databázi.  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a>Příklad  
 Následující příklad spočítá počet produktů v databázi, které nebyly ukončeny.  
  
 Spuštění tohoto příkladu pro ukázkovou databázi Northwind vytvoří výstup `69`.  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Agregační dotazy](aggregate-queries.md)
- [Stažení ukázkových databází](downloading-sample-databases.md)
