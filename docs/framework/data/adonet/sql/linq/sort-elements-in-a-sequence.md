---
title: Řazení prvků v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
ms.openlocfilehash: 21fa2f9e1dc2f255fe94f2420ba90a809ab5b05e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792672"
---
# <a name="sort-elements-in-a-sequence"></a>Řazení prvků v posloupnosti
<xref:System.Linq.Enumerable.OrderBy%2A> Použijte operátor pro řazení pořadí podle jednoho nebo více klíčů.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]je navržena pro podporu řazení podle jednoduchých primitivních typů, `string`například `int`, a tak dále. Nepodporuje řazení složitých tříd s více hodnotami, jako jsou například anonymní typy. Nepodporuje také `byte` typy DataTypes.  
  
## <a name="example"></a>Příklad  
 Následující příklad seřadí `Employees` podle data přijetí.  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `where` k řazení `Orders` expedovaného do `London` dopravného.  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a>Příklad  
 Následující příklad seřadí `Products` podle jednotkové ceny od nejvyšší po nejnižší.  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá složené `OrderBy` pro řazení `Customers` podle města a potom podle jména kontaktu.  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a>Příklad  
 Následující příklad seřadí objednávky od `EmployeeID 1` z `ShipCountry`a pak podle nejvyšších po nejnižší dopravného.  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kombinuje <xref:System.Linq.Enumerable.OrderBy%2A>operátory, <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.GroupBy%2A> aknalezenínejvyššíjednotkovécenyvkaždékategoriianásledněseřadíseskupenípodleIDkategorie.`Products`  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 Pokud spustíte předchozí dotaz na ukázkovou databázi Northwind, výsledky budou vypadat přibližně takto:  
  
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

- [Příklady dotazů](query-examples.md)
- [Stažení ukázkových databází](downloading-sample-databases.md)
