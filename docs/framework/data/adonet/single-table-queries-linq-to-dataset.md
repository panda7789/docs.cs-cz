---
title: Dotazy na jednu tabulku (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: 8807125bd61c71217ca96f3b5a38148ed100073b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794372"
---
# <a name="single-table-queries-linq-to-dataset"></a>Dotazy na jednu tabulku (LINQ to DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]dotazy fungují na zdrojích dat, které <xref:System.Collections.Generic.IEnumerable%601> implementují rozhraní <xref:System.Linq.IQueryable%601> nebo rozhraní. <xref:System.Data.DataTable> <xref:System.Data.DataTableExtensions.AsEnumerable%2A> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] `From` Třída neimplementuje žádné rozhraní, takže je nutné volat metodu, pokud chcete použít jako zdroj v klauzuli dotazu. <xref:System.Data.DataTable>  
  
 Následující příklad načte všechny online objednávky z tabulky SalesOrderHeader a vypíše ID objednávky, datum objednávky a číslo objednávky do konzoly.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)] 
  
 Místní dotaz na proměnnou je inicializován pomocí výrazu dotazu, který pracuje na jednom nebo více zdrojích informací pomocí jednoho nebo více zdrojů pro dotazování buď ze standardních operátorů dotazu, nebo v případě LINQ to DataSet operátory specifické pro <xref:System.Data.DataSet>třída. Výraz dotazu v předchozím příkladu používá dva ze standardních operátorů dotazu: `Where` a. `Select`  
  
 Klauzule filtruje sekvenci na základě podmínky, v tomto případě `OnlineOrderFlag` je nastavena na `true`. `Where` `Select` Operátor přiděluje a vrátí vyčíslitelného objektu, který zachycuje argumenty předané do operátoru. V tomto příkladu je vytvořen anonymní typ se třemi vlastnostmi: `SalesOrderID`, `OrderDate`a `SalesOrderNumber`. Hodnoty těchto tří vlastností jsou `SalesOrderID`nastaveny na hodnoty sloupců, `OrderDate`a `SalesOrderNumber` z `SalesOrderHeader` tabulky.  
  
 Smyčka pak vytvoří výčet vyčíslitelného objektu `Select` vráceného a výsledkem výsledků dotazu. `foreach` Vzhledem k tomu, <xref:System.Linq.Enumerable> že je dotaz typu <xref:System.Collections.Generic.IEnumerable%601>, který implementuje, je vyhodnocování dotazu odloženo, dokud se proměnná dotazu `foreach` neopakuje pomocí smyčky. Odložené vyhodnocování dotazů umožňuje uchovávat dotazy jako hodnoty, které lze vyhodnotit několikrát, pokaždé, když se zaměří na potenciálně odlišné výsledky.  
  
 Metoda poskytuje přístup k hodnotám <xref:System.Data.DataRow> sloupců a a <xref:System.Data.DataRowExtensions.SetField%2A> (nezobrazuje se v <xref:System.Data.DataRow>předchozím příkladu) nastaví hodnoty sloupce v. <xref:System.Data.DataRowExtensions.Field%2A> <xref:System.Data.DataRowExtensions.Field%2A> Metoda i<xref:System.Data.DataRowExtensions.SetField%2A> Metoda zpracovává typy s možnou hodnotou null, takže nemusíte explicitně kontrolovat hodnoty null. Obě metody jsou obecné metody, což znamená, že nemusíte přetypování návratový typ. Můžete použít již existující přistupující objekt sloupce v ( <xref:System.Data.DataRow> `o["OrderDate"]`například), ale v takovém případě by to vyžadovalo přetypování návratového objektu na příslušný typ.  Pokud sloupec může mít hodnotu null, je nutné ověřit, zda je hodnota null pomocí <xref:System.Data.DataRow.IsNull%2A> metody. Další informace naleznete v tématu [generické metody Field a SetField](generic-field-and-setfield-methods-linq-to-dataset.md).  
  
 Všimněte si, že datový typ zadaný v obecném `T` parametru <xref:System.Data.DataRowExtensions.Field%2A> metody a <xref:System.Data.DataRowExtensions.SetField%2A> metody se musí shodovat s typem zdrojové hodnoty nebo dojde k <xref:System.InvalidCastException> vyvolání. Zadaný název sloupce musí také odpovídat názvu sloupce v <xref:System.Data.DataSet> <xref:System.ArgumentException> nebo dojde k vyvolání. V obou případech je výjimka vyvolána při spuštění dotazu při spuštění výčtu dat.  
  
## <a name="see-also"></a>Viz také:

- [Dotazy na křížovou tabulku](cross-table-queries-linq-to-dataset.md)
- [Dotazy na typové datové sady](querying-typed-datasets.md)
- [Obecné pole a metody SetField](generic-field-and-setfield-methods-linq-to-dataset.md)
