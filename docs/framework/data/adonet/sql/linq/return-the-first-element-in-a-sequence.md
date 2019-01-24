---
title: Vrácení prvního prvku v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 74280b0da0713ae089178449fd7fcd0de39e7f9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546673"
---
# <a name="return-the-first-element-in-a-sequence"></a>Vrácení prvního prvku v posloupnosti
Použití <xref:System.Linq.Enumerable.First%2A> operátor vrátí první prvek v sekvenci. Dotazy, které používají <xref:System.Linq.Enumerable.First%2A> provádějí okamžitě.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nepodporuje <xref:System.Linq.Enumerable.Last%2A> operátor.  
  
## <a name="example"></a>Příklad  
 Následující kód najde první `Shipper` v tabulce:  
  
 Pokud spouštíte skript v ukázkové databázi Northwind tento dotaz, jsou výsledky  
  
 `ID = 1, Company = Speedy Express`.  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a>Příklad  
 Následující kód najde jedné `Customer` , který má `CustomerID` BONAP.  
  
 Pokud spouštíte skript v ukázkové databázi Northwind tento dotaz, výsledky jsou `ID = BONAP, Contact = Laurence Lebihan`.  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a>Viz také:
- [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
