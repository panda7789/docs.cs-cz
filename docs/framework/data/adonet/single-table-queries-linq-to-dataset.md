---
title: Dotazy na jednu tabulku (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: 1f4462f617eb81d30f893b52bdc674e1eee8961c
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634765"
---
# <a name="single-table-queries-linq-to-dataset"></a>Dotazy na jednu tabulku (LINQ to DataSet)
Dotazy LINQ (Language-Integrated Query) fungují na zdrojích dat, které implementují rozhraní <xref:System.Collections.Generic.IEnumerable%601> nebo rozhraní <xref:System.Linq.IQueryable%601>. Třída <xref:System.Data.DataTable> neimplementuje žádné rozhraní, takže je nutné volat metodu <xref:System.Data.DataTableExtensions.AsEnumerable%2A>, pokud chcete použít <xref:System.Data.DataTable> jako zdroj v klauzuli `From` dotazu LINQ.  
  
 Následující příklad načte všechny online objednávky z tabulky SalesOrderHeader a vypíše ID objednávky, datum objednávky a číslo objednávky do konzoly.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)] 
  
 Místní dotaz na proměnnou je inicializován pomocí výrazu dotazu, který pracuje na jednom nebo více zdrojích informací pomocí jednoho nebo více zdrojů pro dotazování buď ze standardních operátorů dotazu, nebo v případě LINQ to DataSet operátory specifické pro <xref:System.Data.DataSet> třídy. Výraz dotazu v předchozím příkladu používá dva ze standardních operátorů dotazu: `Where` a `Select`.  
  
 Klauzule `Where` filtruje sekvenci na základě podmínky, v tomto případě je `OnlineOrderFlag` nastavena na `true`. Operátor `Select` přiděluje a vrací vyčíslitelné objekt, který zachycuje argumenty předané do operátoru. V tomto příkladu je vytvořen anonymní typ se třemi vlastnostmi: `SalesOrderID`, `OrderDate`a `SalesOrderNumber`. Hodnoty těchto tří vlastností jsou nastaveny na hodnoty `SalesOrderID`, `OrderDate`a `SalesOrderNumber` sloupců z tabulky `SalesOrderHeader`.  
  
 `foreach` cyklus potom vytvoří výčet vyčíslitelného objektu vráceného `Select` a výsledkem výsledků dotazu. Vzhledem k tomu, že je dotaz typu <xref:System.Linq.Enumerable>, který implementuje <xref:System.Collections.Generic.IEnumerable%601>, vyhodnocování dotazu je odloženo, dokud se proměnná dotazu neprojde pomocí `foreach` smyčky. Odložené vyhodnocování dotazů umožňuje uchovávat dotazy jako hodnoty, které lze vyhodnotit několikrát, pokaždé, když se zaměří na potenciálně odlišné výsledky.  
  
 Metoda <xref:System.Data.DataRowExtensions.Field%2A> poskytuje přístup k hodnotám sloupců <xref:System.Data.DataRow> a <xref:System.Data.DataRowExtensions.SetField%2A> (neuvedené v předchozím příkladu) nastaví hodnoty sloupce v <xref:System.Data.DataRow>. Metoda <xref:System.Data.DataRowExtensions.Field%2A> a metoda <xref:System.Data.DataRowExtensions.SetField%2A> zpracovávají typy s možnou hodnotou null, takže nemusíte explicitně kontrolovat hodnoty null. Obě metody jsou obecné metody, což znamená, že nemusíte přetypování návratový typ. Můžete použít již existující přistupující objekt Column v <xref:System.Data.DataRow> (například `o["OrderDate"]`), ale v takovém případě by to vyžadovalo přetypování návratového objektu na příslušný typ.  Pokud sloupec může mít hodnotu null, je nutné ověřit, zda je hodnota null pomocí metody <xref:System.Data.DataRow.IsNull%2A>. Další informace naleznete v tématu [generické metody Field a SetField](generic-field-and-setfield-methods-linq-to-dataset.md).  
  
 Všimněte si, že datový typ zadaný v obecném parametru `T` metody <xref:System.Data.DataRowExtensions.Field%2A> a metoda <xref:System.Data.DataRowExtensions.SetField%2A> se musí shodovat s typem zdrojové hodnoty nebo bude vyvolána <xref:System.InvalidCastException>. Zadaný název sloupce musí také odpovídat názvu sloupce v <xref:System.Data.DataSet> nebo bude vyvolána <xref:System.ArgumentException>. V obou případech je výjimka vyvolána při spuštění dotazu při spuštění výčtu dat.  
  
## <a name="see-also"></a>Viz také:

- [Dotazy na křížovou tabulku](cross-table-queries-linq-to-dataset.md)
- [Dotazy na typové datové sady](querying-typed-datasets.md)
- [Obecné pole a metody SetField](generic-field-and-setfield-methods-linq-to-dataset.md)
