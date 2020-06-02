---
title: Vytvoření objektu DataTable z dotazu (LINQ to DataSet)
description: Naučte se používat metodu CopyToDataTable k převzetí výsledků dotazu a zkopírování dat do objektu DataTable, který je možné použít pro datovou vazbu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
ms.openlocfilehash: 0a7c8f005b90484ef2f9c7e48218bda40533696a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287009"
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a>Vytvoření objektu DataTable z dotazu (LINQ to DataSet)
Datová vazba je běžné použití <xref:System.Data.DataTable> objektu. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Metoda přijímá výsledky dotazu a kopíruje data do <xref:System.Data.DataTable> , které lze následně použít pro datovou vazbu. Po provedení operací s daty <xref:System.Data.DataTable> se nový sloučí zpátky do zdroje <xref:System.Data.DataTable> .  
  
 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Metoda používá následující proces k vytvoření <xref:System.Data.DataTable> z dotazu:  
  
1. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Metoda naklonuje <xref:System.Data.DataTable> ze zdrojové tabulky ( <xref:System.Data.DataTable> objekt, který implementuje <xref:System.Linq.IQueryable%601> rozhraní). <xref:System.Collections.IEnumerable>Zdroj obecně pochází z výrazu LINQ to DataSet nebo dotazu metody.  
  
2. Schéma klonování <xref:System.Data.DataTable> je postavené ze sloupců prvního výčtového <xref:System.Data.DataRow> objektu ve zdrojové tabulce a názvem klonované tabulky je název zdrojové tabulky, ke které se připojí Word "dotaz".  
  
3. Pro každý řádek ve zdrojové tabulce se obsah řádku zkopíruje do nového <xref:System.Data.DataRow> objektu, který je pak vložen do klonované tabulky. <xref:System.Data.DataRow.RowState%2A>Vlastnosti a <xref:System.Data.DataRow.RowError%2A> jsou zachovány v rámci operace kopírování. <xref:System.ArgumentException>Pokud <xref:System.Data.DataRow> jsou objekty ve zdroji z různých tabulek, je vyvolána výjimka.  
  
4. Klonování <xref:System.Data.DataTable> se vrátí po <xref:System.Data.DataRow> zkopírování všech objektů ve vstupní tabulce Queryable. Pokud zdrojová sekvence neobsahuje žádné <xref:System.Data.DataRow> objekty, metoda vrátí prázdnou hodnotu <xref:System.Data.DataTable> .  
  
Volání <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody způsobí provedení dotazu vázaného na zdrojovou tabulku.  
  
 Když <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metoda nalezne buď odkaz na hodnotu null nebo typ hodnoty s možnou hodnotou null v řádku ve zdrojové tabulce, nahradí hodnotu hodnotou <xref:System.DBNull.Value> . Tímto způsobem se hodnoty null zpracovávají správně ve vrácených hodnotách <xref:System.Data.DataTable> .  
  
 Poznámka: <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda přijímá jako vstup dotaz, který může vracet řádky z více <xref:System.Data.DataTable> objektů nebo <xref:System.Data.DataSet> . <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Metoda zkopíruje data, ale nikoli vlastnosti ze zdroje <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> objektů do vráceného objektu <xref:System.Data.DataTable> . Budete muset explicitně nastavit vlastnosti vrácených <xref:System.Data.DataTable> , například <xref:System.Data.DataTable.Locale%2A> a <xref:System.Data.DataTable.TableName%2A> .  
  
 Následující příklad vyhledá tabulku SalesOrderHeader pro objednávky po 8. srpna 2001 a použije <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metodu k vytvoření <xref:System.Data.DataTable> z tohoto dotazu. <xref:System.Data.DataTable>Je pak svázán s <xref:System.Windows.Forms.BindingSource> , který funguje jako proxy pro <xref:System.Windows.Forms.DataGridView> .  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a>Vytvoření vlastní metody CopyToDataTable \<T>  
 Stávající <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody fungují pouze ve <xref:System.Collections.Generic.IEnumerable%601> zdroji, kde je obecný parametr `T` typu <xref:System.Data.DataRow> . I když je to užitečné, neumožňuje vytvářet tabulky ze sekvence skalárních typů, od dotazů, které vracejí anonymní typy, nebo z dotazů, které provádějí spojení tabulek. Příklad toho, jak implementovat dvě vlastní `CopyToDataTable` metody, které načítají tabulku ze sekvence skalárních nebo anonymních typů, naleznete v tématu [How to: Implement CopyToDataTable, \<T> kde obecný typ T není DataRow](implement-copytodatatable-where-type-not-a-datarow.md)s.  
  
 Příklady v této části používají následující vlastní typy:  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a>Příklad  
 Tento příklad provede spojení `SalesOrderHeader` tabulek a a `SalesOrderDetail` získá online objednávky z měsíce srpna a vytvoří tabulku z dotazu.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#join)]
 [!code-vb[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#join)]  
  
### <a name="example"></a>Příklad  
 Následující příklad dotazuje kolekci pro položky Price větší než $9,99 a vytvoří tabulku z výsledků dotazu.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintotable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintotable)]  
  
### <a name="example"></a>Příklad  
 Následující příklad dotazuje kolekci pro položky Price větší než 9,99 a výsledky projektů. Vrácená sekvence anonymních typů je načtena do existující tabulky.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintoexistingtable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintoexistingtable)]  
  
### <a name="example"></a>Příklad  
 Následující příklad dotazuje kolekci pro položky Price větší než $9,99 a výsledky projektů. Vrácená sekvence anonymních typů je načtena do existující tabulky. Schéma tabulky je automaticky rozbaleno, protože `Book` `Movies` typy a jsou odvozeny z `Item` typu.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a>Příklad  
 Následující příklad vyhledá kolekci pro položky Price větší než $9,99 a vrátí sekvenci <xref:System.Double> , která je načtena do nové tabulky.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním](programming-guide-linq-to-dataset.md)
- [Obecné pole a metody SetField](generic-field-and-setfield-methods-linq-to-dataset.md)
- [Příklady LINQ to DataSet](linq-to-dataset-examples.md)
