---
title: Nalezení maximální hodnoty v číselné posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
ms.openlocfilehash: ebef8cb373da4021fd68fd7ce38de8cb06eb81ec
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782181"
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a>Nalezení maximální hodnoty v číselné posloupnosti
<xref:System.Linq.Enumerable.Max%2A> Použijte operátor k vyhledání nejvyšší hodnoty v posloupnosti číselných hodnot.  
  
## <a name="example"></a>Příklad  
 Následující příklad najde poslední datum zařazení pro každého zaměstnance.  
  
 Pokud spustíte tento dotaz proti ukázkové databázi Northwind, výstup je: `11/15/1994 12:00:00 AM`.  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad najde nejvíc jednotek na skladě pro libovolný produkt.  
  
 Pokud tento příklad spustíte s ukázkovou databází Northwind, výstup je: `125`.  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá Max k nalezení `Products` nejvyšší jednotkové ceny v každé kategorii. Výstup pak zobrazí výsledky podle kategorie.  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 Pokud spustíte předchozí dotaz na ukázkovou databázi Northwind, výsledky budou vypadat takto:  
  
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

- [Agregační dotazy](aggregate-queries.md)
- [Stažení ukázkových databází](downloading-sample-databases.md)
