---
title: Vrátí maximální hodnotu číselného pořadí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
ms.openlocfilehash: c93b322c755036c8bf7150bb5c96b9c32b6dc9b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353814"
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a>Vrátí maximální hodnotu číselného pořadí
Použití <xref:System.Linq.Enumerable.Max%2A> operátor a vyhledá nejvyšší hodnotu v sekvenci číselné hodnoty.  
  
## <a name="example"></a>Příklad  
 Následující příklad vyhledá nejnovější data přijetím pro všechny zaměstnance.  
  
 Pokud spustíte tento dotaz pro ukázkové databázi Northwind, je výstup: `11/15/1994 12:00:00 AM`.  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vyhledá v stock většina jednotky pro některý z produktů.  
  
 Pokud spustíte v tomto příkladu v ukázkové databázi Northwind, je výstup: `125`.  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá k nalezení maximální `Products` které mají nejvyšší jednotkové ceny v každé kategorii. Výstup jsou výsledky pak uvedené podle kategorie.  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 Pokud spustíte předchozí dotaz proti ukázková databáze Northwind, výsledky budou vypadat takto:  
  
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
  
## <a name="see-also"></a>Viz také  
 [Agregační dotazy](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
