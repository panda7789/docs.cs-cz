---
title: Nalezení maximální hodnoty v číselné posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
ms.openlocfilehash: b7a2588b9e5082915dff4d371adff2ad3d232d74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032536"
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a>Nalezení maximální hodnoty v číselné posloupnosti
Použití <xref:System.Linq.Enumerable.Max%2A> operátor vyhledá nejvyšší hodnotu v pořadí číselných hodnot.  
  
## <a name="example"></a>Příklad  
 Následující příklad vyhledá poslední datum zařazení pro všechny zaměstnance.  
  
 Pokud spouštíte skript v ukázkové databázi Northwind tento dotaz, je výstup: `11/15/1994 12:00:00 AM`.  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vyhledá většina jednotky v zásobách pro některý z produktů.  
  
 Pokud spouštíte skript v ukázkové databázi Northwind v tomto příkladu, výstup je: `125`.  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá k nalezení maximální `Products` , které mají nejvyšší cena za jednotku v jednotlivých kategoriích. Výstup zobrazí výsledky podle kategorií.  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 Pokud spustíte předchozí dotaz s ukázkovou databází Northwind, vaše výsledky budou vypadat takto:  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a>Viz také:

- [Agregační dotazy](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
