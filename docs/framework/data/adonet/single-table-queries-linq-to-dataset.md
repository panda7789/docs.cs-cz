---
title: Dotazy na jednu tabulku (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: 3bde9a5f718dcc7bdf31f84369546d530dca38d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637245"
---
# <a name="single-table-queries-linq-to-dataset"></a>Dotazy na jednu tabulku (LINQ to DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] dotazy fungují u zdrojů dat, které implementují <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo <xref:System.Linq.IQueryable%601> rozhraní. <xref:System.Data.DataTable> Třída neimplementuje buď rozhraní, takže je třeba zavolat <xref:System.Data.DataTableExtensions.AsEnumerable%2A> metodu, pokud chcete použít <xref:System.Data.DataTable> jako zdroj v `From` klauzuli [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazu.  
  
 Následující příklad získá online objednávky z tabulky SalesOrderHeader a vypíše ID objednávky, data objednávky a pořadové číslo do konzoly.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)] 
  
 Místní proměnná dotazu je inicializován pomocí výrazu dotazu, které působí na jeden nebo více zdrojů informace s použitím jednoho nebo více operátorů dotazu, buď z operátory standardního dotazu, nebo v případě [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], operátory, které jsou specifické pro <xref:System.Data.DataSet>třídy. Výraz dotazu v předchozím příkladu používá dva operátory standardního dotazu: `Where` a `Select`.  
  
 `Where` Klauzule filtry pořadí na základě podmínky, v tomto případě, že `OnlineOrderFlag` je nastavena na `true`. `Select` Operátor přiděluje a vrací vyčíslitelný objekt, který zachycuje argumentů předaný operátoru. V tomto nad příkladu se vytvoří anonymního typu s tři vlastnosti: `SalesOrderID`, `OrderDate`, a `SalesOrderNumber`. Hodnoty tyto tři vlastnosti jsou nastaveny na hodnoty `SalesOrderID`, `OrderDate`, a `SalesOrderNumber` sloupce z `SalesOrderHeader` tabulky.  
  
 `foreach` Smyčky pak vytvoří výčet vyčíslitelný objekt vrácený rutinou `Select` a vrací výsledky dotazu. Vzhledem k tomu, že dotaz je <xref:System.Linq.Enumerable> zadejte, která implementuje <xref:System.Collections.Generic.IEnumerable%601>, vyhodnocení dotazu je odloženo, dokud není procházen proměnné dotazu pomocí `foreach` smyčky. Odložený dotaz hodnocení umožňuje vytvářet dotazy průběžně podle hodnoty, které mohou být vyhodnoceny několikrát, pokaždé, když získávání potenciálně odlišné výsledky.  
  
 <xref:System.Data.DataRowExtensions.Field%2A> Metoda poskytuje přístup k hodnoty sloupce <xref:System.Data.DataRow> a <xref:System.Data.DataRowExtensions.SetField%2A> (není vidět v předchozím příkladu) nastaví hodnoty ve sloupcích v <xref:System.Data.DataRow>. Oba <xref:System.Data.DataRowExtensions.Field%2A> metoda a <xref:System.Data.DataRowExtensions.SetField%2A> metoda zpracování typy připouštějící hodnotu Null, takže není potřeba explicitně kontrola hodnot null. Obě metody jsou obecné metody, také, což znamená, že není nutné přetypovat návratový typ. Můžete použít už existující přistupující objekt sloupce v <xref:System.Data.DataRow> (například `o["OrderDate"]`), ale to uděláte tak by vyžadovalo přetypovat vrácený objekt do příslušného typu.  Pokud je sloupec s možnou hodnotou Null, budete muset zkontrolovat, zda je hodnota null pomocí <xref:System.Data.DataRow.IsNull%2A> metody. Další informace najdete v tématu [obecné pole a metody SetField](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md).  
  
 Všimněte si, že datový typ zadaný v parametru obecného `T` z <xref:System.Data.DataRowExtensions.Field%2A> metoda a <xref:System.Data.DataRowExtensions.SetField%2A> metoda musí odpovídat typu základní hodnotu nebo <xref:System.InvalidCastException> bude vyvolána výjimka. Zadaný název sloupce musí taky shodovat s názvem sloupce v <xref:System.Data.DataSet> nebo <xref:System.ArgumentException> bude vyvolána výjimka. V obou případech je vyvolána výjimka za běhu výčet dat při spuštění dotazu.  
  
## <a name="see-also"></a>Viz také:
- [Dotazy na křížovou tabulku](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)
- [Dotazy na typové datové sady](../../../../docs/framework/data/adonet/querying-typed-datasets.md)
- [Obecné pole a metody SetField](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)
