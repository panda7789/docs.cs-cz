---
title: Vrácení prvního prvku v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 9faeed754942d7b176872484ac776c1df592bbd8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792719"
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

- [Příklady dotazů](query-examples.md)
- [Stažení ukázkových databází](downloading-sample-databases.md)
