---
title: "Vrátí maximální hodnotu číselného pořadí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 387fe8db55da337b970bbac0e6e046b43433b482
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
