---
title: Vrácení prvního prvku v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 39cf9270b08fce64590fef418bb428c5a781b0e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963810"
---
# <a name="return-the-first-element-in-a-sequence"></a>Vrácení prvního prvku v posloupnosti
<xref:System.Linq.Enumerable.First%2A> Použijte operátor k vrácení prvního prvku v sekvenci. Dotazy, které <xref:System.Linq.Enumerable.First%2A> používají, se spustí okamžitě.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Linq.Enumerable.Last%2A> nepodporuje operátor.  
  
## <a name="example"></a>Příklad  
 Následující kód vyhledá první `Shipper` v tabulce:  
  
 Pokud spustíte tento dotaz proti ukázkové databázi Northwind, výsledky jsou  
  
 `ID = 1, Company = Speedy Express`.  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a>Příklad  
 Následující kód najde jeden `Customer` , který `CustomerID` má BONAP.  
  
 Pokud spustíte tento dotaz proti ukázkové databázi Northwind, budou `ID = BONAP, Contact = Laurence Lebihan`výsledky.  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
