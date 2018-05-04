---
title: Vytváření DataTable z dotazu (LINQ na DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
ms.openlocfilehash: f4ea8749c6e1c853f87f17e735887bbdd4d72e2a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a>Vytváření DataTable z dotazu (LINQ na DataSet)
Datová vazba se běžně používá z <xref:System.Data.DataTable> objektu. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda přebírá výsledky dotazu a zkopíruje data do <xref:System.Data.DataTable>, který pak může být použit pro datovou vazbu. Pokud operace dat prováděly, nové <xref:System.Data.DataTable> je sloučen zpět do zdroje <xref:System.Data.DataTable>.  
  
 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda používá následující postup k vytvoření <xref:System.Data.DataTable> z dotazu:  
  
1.  <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda klony <xref:System.Data.DataTable> ze zdrojové tabulky ( <xref:System.Data.DataTable> objekt, který implementuje <xref:System.Linq.IQueryable%601> rozhraní). <xref:System.Collections.IEnumerable> Zdroj je obvykle pochází z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] metoda nebo výraz dotazu.  
  
2.  Schéma klonované <xref:System.Data.DataTable> je sestaven z prvního sloupce ve výčtu <xref:System.Data.DataRow> objekt ve zdrojové tabulky a název klonovaného tabulky je název zdrojové tabulky slovem "dotaz" k němu připojen.  
  
3.  Pro každý řádek ve zdrojové tabulce obsah řádek zkopírován do nového <xref:System.Data.DataRow> objekt, který se pak vloží do klonovaný tabulky. <xref:System.Data.DataRow.RowState%2A> a <xref:System.Data.DataRow.RowError%2A> vlastnosti jsou zachovány v operaci kopírování. <xref:System.ArgumentException> Je vyvolána, pokud <xref:System.Data.DataRow> objekty ve zdroji jsou z různých tabulek.  
  
4.  Klonované <xref:System.Data.DataTable> se vrátí po všech <xref:System.Data.DataRow> objekty ve vstupní tabulce dotazovatelný byly zkopírovány. Pokud zdrojové sekvence neobsahuje žádný <xref:System.Data.DataRow> objektů, metoda vrátí prázdnou <xref:System.Data.DataTable>.  
  
 Všimněte si, že volání <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> způsobí, že metoda vázán na zdrojové tabulky pro spuštění dotazu.  
  
 Když <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metoda zaznamená buď odkazu s hodnotou null, nebo typ s možnou hodnotou Null hodnoty v řádku ve zdrojové tabulce, se nahradí hodnotu s <xref:System.DBNull.Value>. Tímto způsobem, hodnoty null zpracovává správně ve vráceném <xref:System.Data.DataTable>.  
  
 Poznámka: <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metoda akceptuje jako vstupní dotaz, který může vrátit řádky z několika <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> objekty. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda zkopíruje data, ale ne vlastnosti ze zdroje <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> objektů vrácený <xref:System.Data.DataTable>. Je potřeba explicitně nastavit vlastnosti na vrácený <xref:System.Data.DataTable>, jako například <xref:System.Data.DataTable.Locale%2A> a <xref:System.Data.DataTable.TableName%2A>.  
  
 V následujícím příkladu dotazuje tabulku SalesOrderHeader pro objednávky po 8. srpna 2001 a používá <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metodu pro vytvoření <xref:System.Data.DataTable> z tohoto dotazu. <xref:System.Data.DataTable> Pak je vázána <xref:System.Windows.Forms.BindingSource>, který funguje jako proxy server pro <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a>Vytváření vlastních CopyToDataTable\<T > – metoda  
 Existující <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody pracovat pouze v <xref:System.Collections.Generic.IEnumerable%601> zdroje kde obecný parametr `T` je typu <xref:System.Data.DataRow>. I když to je užitečné, neumožňuje tabulky má být vytvořen z posloupnost Skalární typy, dotazy, které vracejí anonymní typy nebo dotazy, které provádějí spoje tabulky platná. Příklad toho, jak implementovat dvě vlastní `CopyToDataTable` metody, které načíst tabulku z řady typů skalární nebo anonymní, najdete v části [postupy: implementace CopyToDataTable\<T > kde the obecný typ T Is Not DataRow](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)s.  
  
 Příklady v této části použijte následující vlastní typy:  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a>Příklad  
 Tento příklad spojí přes `SalesOrderHeader` a `SalesOrderDetail` tabulky, chcete-li získat online objednávky z srpnu a vytvoří tabulku z dotazu.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#join)]
 [!code-vb[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#join)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu dotazuje kolekci pro ceny, které jsou větší než $9.99 a vytvoří tabulku z výsledků dotazu.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintotable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintotable)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu dotazuje kolekci pro větší než 9.99 ceny a projekty výsledky. Vrácený pořadí anonymní typy je načten do existující tabulky.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintoexistingtable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintoexistingtable)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu dotazuje kolekci pro ceny, které jsou větší než $9.99 a projekty výsledky. Vrácený pořadí anonymní typy je načten do existující tabulky. Schéma tabulky je automaticky rozšířena, protože `Book` a `Movies` typy jsou odvozeny od `Item` typu.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu dotazuje kolekci pro ceny, které jsou větší než $9.99 a vrátí posloupnost <xref:System.Double>, který je načten do nové tabulky.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
 [Obecné pole a metody SetField](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)  
 [Příklady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
