---
title: Vytvoření datové tabulky z dotazu (LINQ do dataset)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
ms.openlocfilehash: 46e977088cd6eca7842565ae6b258f70ca5920a9
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111813"
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a>Vytvoření datové tabulky z dotazu (LINQ do dataset)
Datová vazba je <xref:System.Data.DataTable> běžné použití objektu. Metoda <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> přebírá výsledky dotazu a zkopíruje <xref:System.Data.DataTable>data do , který pak lze použít pro datové vazby. Po provedení operací s daty <xref:System.Data.DataTable> je novinka sloučena zpět do zdroje <xref:System.Data.DataTable>.  
  
 Metoda <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> používá následující proces k <xref:System.Data.DataTable> vytvoření z dotazu:  
  
1. Metoda <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> klonuje <xref:System.Data.DataTable> ze zdrojové <xref:System.Data.DataTable> tabulky (objekt, <xref:System.Linq.IQueryable%601> který implementuje rozhraní). Zdroj <xref:System.Collections.IEnumerable> má obecně pochází z LINQ do DataSet výraz nebo dotaz metody.  
  
2. Schéma klonovaného <xref:System.Data.DataTable> je sestaveno ze sloupců prvního výčtového <xref:System.Data.DataRow> objektu ve zdrojové tabulce a název klonované tabulky je název zdrojové tabulky se slovem "dotaz".  
  
3. Pro každý řádek ve zdrojové tabulce je obsah řádku <xref:System.Data.DataRow> zkopírován do nového objektu, který je pak vložen do klonované tabulky. <xref:System.Data.DataRow.RowState%2A> Vlastnosti <xref:System.Data.DataRow.RowError%2A> a jsou zachovány v celé operaci kopírování. Je <xref:System.ArgumentException> vyvolána, <xref:System.Data.DataRow> pokud objekty ve zdroji jsou z různých tabulek.  
  
4. Klonovaný <xref:System.Data.DataTable> je vrácena <xref:System.Data.DataRow> po všechny objekty ve vstupní dotazovatelné tabulky byly zkopírovány. Pokud zdrojová sekvence neobsahuje žádné <xref:System.Data.DataRow> objekty, <xref:System.Data.DataTable>metoda vrátí prázdné .  
  
Volání <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody způsobí, že dotaz vázán na zdrojovou tabulku spustit.  
  
 Pokud <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metoda narazí buď na hodnotu null, nebo na typ hodnoty s možnou <xref:System.DBNull.Value>hodnotou null v řádku ve zdrojové tabulce, nahradí hodnotu hodnotou . Tímto způsobem jsou hodnoty null <xref:System.Data.DataTable>správně zpracovány ve vráceném .  
  
 Poznámka: <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda přijímá jako vstupní dotaz, který <xref:System.Data.DataTable> může <xref:System.Data.DataSet> vrátit řádky z více nebo objektů. Metoda <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> zkopíruje data, ale ne vlastnosti <xref:System.Data.DataSet> ze zdroje <xref:System.Data.DataTable> <xref:System.Data.DataTable> nebo objektů do vrácených . Budete muset explicitně nastavit vlastnosti <xref:System.Data.DataTable>na <xref:System.Data.DataTable.Locale%2A> vrácené , například a <xref:System.Data.DataTable.TableName%2A>.  
  
 Následující příklad se dotazuje tabulky SalesOrderHeader na objednávky po <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 8. <xref:System.Data.DataTable> Je <xref:System.Data.DataTable> pak vázána <xref:System.Windows.Forms.BindingSource>na , který <xref:System.Windows.Forms.DataGridView>působí jako proxy pro .  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a>Vytvoření metody> vlastní\<tabulky CopyToDataTable T  
 Existující <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody pracují pouze <xref:System.Collections.Generic.IEnumerable%601> na zdroj, `T` kde <xref:System.Data.DataRow>je obecný parametr typu . I když je to užitečné, neumožňuje tabulky, které mají být vytvořeny z posloupnosti skalární typy, z dotazů, které vracejí anonymní typy nebo z dotazů, které provádějí spojení tabulky. Příklad, jak implementovat dvě `CopyToDataTable` vlastní metody, které načítají tabulku z posloupnosti skalární nebo anonymní typy, naleznete v [tématu How to:\<Implement CopyToDataTable T> Where the Generic Type T Is Not a DataRow](implement-copytodatatable-where-type-not-a-datarow.md)s.  
  
 Příklady v této části používají následující vlastní typy:  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a>Příklad  
 Tento příklad provede spojení `SalesOrderHeader` `SalesOrderDetail` přes tabulky a získat online objednávky z měsíce srpna a vytvoří tabulku z dotazu.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#join)]
 [!code-vb[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#join)]  
  
### <a name="example"></a>Příklad  
 Následující příklad dotazuje kolekce pro položky ceny větší než $9.99 a vytvoří tabulku z výsledků dotazu.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintotable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintotable)]  
  
### <a name="example"></a>Příklad  
 Následující příklad dotazuje kolekce pro položky s cenou větší než 9,99 a projekty výsledky. Vrácená posloupnost anonymních typů je načtena do existující tabulky.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintoexistingtable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintoexistingtable)]  
  
### <a name="example"></a>Příklad  
 Následující příklad dotazuje kolekce pro položky cena větší než $9.99 a projekty výsledky. Vrácená posloupnost anonymních typů je načtena do existující tabulky. Schéma tabulky je automaticky `Book` rozbaleno, `Movies` protože typy a `Item` jsou odvozeny od typu.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a>Příklad  
 Následující příklad dotazuje kolekce pro položky ceny větší než $9.99 a vrátí posloupnost <xref:System.Double>, která je načtena do nové tabulky.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka](programming-guide-linq-to-dataset.md)
- [Obecné pole a metody SetField](generic-field-and-setfield-methods-linq-to-dataset.md)
- [Příklady LINQ to DataSet](linq-to-dataset-examples.md)
