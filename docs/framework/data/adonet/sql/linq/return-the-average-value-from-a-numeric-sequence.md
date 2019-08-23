---
title: Vrácení průměrné hodnoty z číselné posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee3b8673-a2e7-4b2d-9b5c-4972ff9e665d
ms.openlocfilehash: 56fe777a3bca1e2b54b61d1586f78a2df4fb475f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963826"
---
# <a name="return-the-average-value-from-a-numeric-sequence"></a>Vrácení průměrné hodnoty z číselné posloupnosti
<xref:System.Linq.Enumerable.Average%2A> Operátor vypočítá průměr posloupnosti číselných hodnot.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Překlad celočíselnýchhodnotjevypočítánjakoceléčíslo,nikolijakotypDouble.`Average`  
  
## <a name="example"></a>Příklad  
 Následující příklad vrátí průměr `Freight` hodnot `Orders` v tabulce.  
  
 Výsledky z ukázkové databáze Northwind budou `78.2442`.  
  
 [!code-csharp[DLinqQueryExamples#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#1)]
 [!code-vb[DLinqQueryExamples#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#1)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vrátí průměr jednotkové ceny všech `Products` `Products` v tabulce.  
  
 Výsledky z ukázkové databáze Northwind budou `28.8663`.  
  
 [!code-csharp[DLinqQueryExamples#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#2)]
 [!code-vb[DLinqQueryExamples#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#2)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Average` operátor k vyhledání těch `Products` , jejichž jednotková cena je vyšší než průměrná cena za jednotku kategorie, do které patří. Příklad zobrazí výsledky ve skupinách.  
  
 Všimněte si, že tento příklad vyžaduje použití `var` klíčového slova v C#, protože návratový typ je anonymní.  
  
 [!code-csharp[DLinqQueryExamples#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#3)]
 [!code-vb[DLinqQueryExamples#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#3)]  
  
 Pokud spustíte tento dotaz proti ukázkové databázi Northwind, výsledky by se měly podobat následujícímu:  
  
 `1`  
  
 `Côte de Blaye`  
  
 `Ipoh Coffee`  
  
 `2`  
  
 `Grandma's Boysenberry Spread`  
  
 `Northwoods Cranberry Sauce`  
  
 `Sirop d'érable`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `Gumbär Gummibärchen`  
  
 `Schoggi Schokolade`  
  
 `Tarte au sucre`  
  
 `4`  
  
 `Queso Manchego La Pastora`  
  
 `Mascarpone Fabioli`  
  
 `Raclette Courdavault`  
  
 `Camembert Pierrot`  
  
 `Gudbrandsdalsost`  
  
 `Mozzarella di Giovanni`  
  
 `5`  
  
 `Gustaf's Knäckebröd`  
  
 `Gnocchi di nonna Alice`  
  
 `Wimmers gute Semmelknödel`  
  
 `6`  
  
 `Mishi Kobe Niku`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Rössle Sauerkraut`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Ikura`  
  
 `Carnarvon Tigers`  
  
 `Nord-Ost Matjeshering`  
  
 `Gravad lax`  
  
## <a name="see-also"></a>Viz také:

- [Agregační dotazy](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
