---
title: Jednotalové dotazy (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: 7bb8d8e19ac9cf36eabc061ceba9c649b8a4cc00
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148969"
---
# <a name="single-table-queries-linq-to-dataset"></a>Jednotalové dotazy (LINQ to DataSet)
Dotazy integrovaného jazyka (LINQ) pracují na zdrojích dat, které implementují <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo <xref:System.Linq.IQueryable%601> rozhraní. Třída <xref:System.Data.DataTable> neimplementuje žádné rozhraní, takže <xref:System.Data.DataTableExtensions.AsEnumerable%2A> je nutné volat <xref:System.Data.DataTable> metodu, pokud `From` chcete použít jako zdroj v klauzuli dotazu LINQ.  
  
 Následující příklad získá všechny online objednávky z tabulky SalesOrderHeader a vyveze ID objednávky, datum objednávky a číslo objednávky do konzoly.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]
  
 Dotaz místní proměnné je inicializován výrazem dotazu, který pracuje s jedním nebo více zdroji informací použitím jednoho nebo více operátorů dotazů <xref:System.Data.DataSet> ze standardních operátorů dotazů nebo v případě LINQ to DataSet operátorů specifických pro danou třídu. Výraz dotazu v předchozím příkladu používá dva `Where` `Select`standardní operátory dotazu: a .  
  
 Klauzule `Where` filtruje sekvenci na základě `OnlineOrderFlag` podmínky, `true`v tomto případě je nastavena na . Operátor `Select` přiděluje a vrací výčtový objekt, který zachycuje argumenty předané operátoru. V tomto výše uvedeném příkladu je `SalesOrderID`vytvořen `OrderDate`anonymní `SalesOrderNumber`typ se třemi vlastnostmi: , a . Hodnoty těchto tří vlastností jsou nastaveny `SalesOrderID` `OrderDate`na `SalesOrderNumber` hodnoty , `SalesOrderHeader` a sloupce z tabulky.  
  
 Smyčka `foreach` pak vytvoří výčet výčtu výčtu objektu vráceného `Select` a výnosy výsledky dotazu. Vzhledem k <xref:System.Linq.Enumerable> tomu, že <xref:System.Collections.Generic.IEnumerable%601>dotaz je typ, který implementuje , je vyhodnocení `foreach` dotazu odloženo, dokud není proměnná dotazu iterována pomocí smyčky. Odložené vyhodnocení dotazu umožňuje dotazy, které mají být uchovávány jako hodnoty, které mohou být vyhodnoceny vícekrát, pokaždé, když dává potenciálně odlišné výsledky.  
  
 Metoda <xref:System.Data.DataRowExtensions.Field%2A> poskytuje přístup k hodnotám <xref:System.Data.DataRow> sloupců a a <xref:System.Data.DataRowExtensions.SetField%2A> (není uvedeno v <xref:System.Data.DataRow>předchozím příkladu) nastaví hodnoty sloupců v . <xref:System.Data.DataRowExtensions.Field%2A> Metody i <xref:System.Data.DataRowExtensions.SetField%2A> metody zpracovávají typy s možnou hodnotou null, takže není třeba explicitně kontrolovat hodnoty null. Obě metody jsou obecné metody, také, což znamená, že není třeba přetypovat návratový typ. Můžete použít již existující přistupující objekt sloupce v <xref:System.Data.DataRow> (například `o["OrderDate"]`), ale přitom by vyžadovalo přetypovat návratový objekt na příslušný typ.  Pokud je sloupec nullable, musíte zkontrolovat, zda je <xref:System.Data.DataRow.IsNull%2A> hodnota null pomocí metody. Další informace naleznete [v tématu Obecné pole a Metody SetField](generic-field-and-setfield-methods-linq-to-dataset.md).  
  
 Všimněte si, že datový `T` typ <xref:System.Data.DataRowExtensions.Field%2A> zadaný <xref:System.Data.DataRowExtensions.SetField%2A> v obecném parametru metody <xref:System.InvalidCastException> a metody musí odpovídat typu podkladové hodnoty nebo bude vyvolána. Zadaný název sloupce musí také odpovídat <xref:System.Data.DataSet> názvu <xref:System.ArgumentException> sloupce v nebo bude vyvolána. V obou případech je výjimka vyvolána při spuštění při spuštění dotazu.  
  
## <a name="see-also"></a>Viz také

- [Dotazy na křížovou tabulku](cross-table-queries-linq-to-dataset.md)
- [Dotazy na typové datové sady](querying-typed-datasets.md)
- [Obecné pole a metody SetField](generic-field-and-setfield-methods-linq-to-dataset.md)
