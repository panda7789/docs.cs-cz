---
title: Vytvoření datové tabulky z dotazu (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
ms.openlocfilehash: fd2b639f98dbb381cf4bea70cc790fd99ebf185f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708347"
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a>Vytvoření datové tabulky z dotazu (LINQ to DataSet)
Datová vazba je běžně <xref:System.Data.DataTable> objektu. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda přijímá výsledky dotazu a zkopíruje data do <xref:System.Data.DataTable>, který potom slouží pro vytváření datových vazeb. Když prováděly operace s daty, nové <xref:System.Data.DataTable> se sloučí zpět do zdroje <xref:System.Data.DataTable>.  
  
 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda používá následující proces vytvoření <xref:System.Data.DataTable> z dotazu:  
  
1.  <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda duplicity <xref:System.Data.DataTable> ze zdrojové tabulky ( <xref:System.Data.DataTable> objekt, který implementuje <xref:System.Linq.IQueryable%601> rozhraní). <xref:System.Collections.IEnumerable> Zdroj má obvykle pochází z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] výraz nebo metodu dotazu.  
  
2.  Schéma klonované <xref:System.Data.DataTable> je sestaven z prvního sloupce ve výčtu <xref:System.Data.DataRow> objektu ve zdrojové tabulce a název klonovaného tabulky je název zdrojové tabulky obsahující slovo "dotazování" připojenou k němu.  
  
3.  Pro každý řádek v tabulce zdrojový obsah řádku, který zkopíruje do nového <xref:System.Data.DataRow> objektu, který se pak vloží do naklonovaného tabulky. <xref:System.Data.DataRow.RowState%2A> a <xref:System.Data.DataRow.RowError%2A> vlastnosti jsou zachovány v operaci kopírování. <xref:System.ArgumentException> Je vyvolána, pokud <xref:System.Data.DataRow> objekty ve zdroji pocházejí z různých tabulek.  
  
4.  Klonované <xref:System.Data.DataTable> se vrátí po všech <xref:System.Data.DataRow> objekty ve vstupní tabulce dotazovatelné byly zkopírovány. Pokud zdrojové sekvence neobsahuje žádný <xref:System.Data.DataRow> objektů, metoda vrátí prázdnou <xref:System.Data.DataTable>.  
  
 Všimněte si, že volání <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> způsobí, že metoda vázán na zdrojovou tabulku k provedení dotazu.  
  
 Když <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metoda zaznamená nulový odkaz nebo typ s možnou hodnotou Null v řádku ve zdrojové tabulce, nahradí hodnotu s <xref:System.DBNull.Value>. Tímto způsobem, hodnoty null jsou zpracovány správně ve vráceném <xref:System.Data.DataTable>.  
  
 Poznámka: <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda přijímá jako vstup dotazu, která vrací řádky z několika <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> objekty. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda zkopíruje data, ale nikoli vlastnosti ze zdroje <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> objekty na vrácenou <xref:System.Data.DataTable>. Je potřeba explicitně nastavit vlastnosti vráceného <xref:System.Data.DataTable>, jako například <xref:System.Data.DataTable.Locale%2A> a <xref:System.Data.DataTable.TableName%2A>.  
  
 V následujícím příkladu dotazuje tabulku SalesOrderHeader pro objednávky po 8. srpna 2001 a používá <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metodu pro vytvoření <xref:System.Data.DataTable> z dotazu. <xref:System.Data.DataTable> Pak je vázán na <xref:System.Windows.Forms.BindingSource>, který funguje jako proxy pro <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a>Vytváření vlastních CopyToDataTable\<T > – metoda  
 Existující <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody pracovat pouze s <xref:System.Collections.Generic.IEnumerable%601> zdroje kde obecný parametr `T` je typu <xref:System.Data.DataRow>. I když to je užitečné, neumožňuje tabulky vytvořit ze sekvence Skalární typy, dotazy, které vracejí anonymních typů nebo dotazy, které provádějí spojování tabulek platná. Příklad toho, jak implementovat dvě vlastní `CopyToDataTable` metody, které načíst tabulku ze sekvence skalární nebo anonymní typy, najdete v článku [jak: Implementace CopyToDataTable\<T > kde obecný typ není DataRow](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)s.  
  
 Příklady v této části používají následující vlastní typy:  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a>Příklad  
 V tomto příkladu provádí spojení `SalesOrderHeader` a `SalesOrderDetail` tabulky k získání online objednávky z srpnu a vytvoří tabulku z dotazu.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#join)]
 [!code-vb[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#join)]  
  
### <a name="example"></a>Příklad  
 Následující příklad dotazuje kolekci položek cena je vyšší než 9,99 USD a vytvoří tabulku z výsledků dotazu.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintotable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintotable)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu dotazuje kolekci položek cena je vyšší než 9,99 a projekty výsledky. Vrácené posloupnosti anonymní typy se načtou do existující tabulky.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintoexistingtable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintoexistingtable)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu dotazuje kolekci položek cena je vyšší než 9,99 USD a projekty výsledky. Vrácené posloupnosti anonymní typy se načtou do existující tabulky. Schéma tabulky se automaticky rozšíří, protože `Book` a `Movies` typy jsou odvozeny z `Item` typu.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu dotazuje kolekci položek cena je vyšší než 9,99 USD a vrátí sekvenci <xref:System.Double>, který je načten do nové tabulky.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a>Viz také:
- [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
- [Obecné pole a metody SetField](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)
- [Příklady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
