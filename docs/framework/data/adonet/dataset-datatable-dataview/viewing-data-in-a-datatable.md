---
title: Zobrazení dat v DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: 5d39d2a856a40b5ea20832a544ede360313309d3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="viewing-data-in-a-datatable"></a>Zobrazení dat v DataTable
Můžete přistupovat k obsahu <xref:System.Data.DataTable> pomocí **řádky** a **sloupce** kolekce **DataTable**. Můžete také <xref:System.Data.DataTable.Select%2A> metoda vrátí podmnožiny dat v **DataTable** podle kritérií, včetně kritéria hledání, pořadí řazení a řádku stavu. Kromě toho můžete použít <xref:System.Data.DataRowCollection.Find%2A> metodu **kolekci DataRowCollection** při hledání konkrétního řádku pomocí hodnotu primárního klíče.  
  
 **Vyberte** metodu **DataTable** objekt vrací sadu <xref:System.Data.DataRow> objekty, které odpovídají zadaným kritériím. **Vyberte** přebírá volitelné argumenty výraz filtru výrazů řazení a **DataViewRowState**. Výraz filtru identifikuje řádky, které chcete vrátit na základě **DataColumn** hodnoty, jako například `LastName = 'Smith'`. Výraz řazení dodržovat standardní SQL konvence pro řazení sloupců, například `LastName ASC, FirstName ASC`. Pravidla o zapisují se výrazy, najdete v článku <xref:System.Data.DataColumn.Expression%2A> vlastnost **DataColumn** třídy.  
  
> [!TIP]
>  Pokud provádíte počet volání **vyberte** metodu **DataTable**, můžete zvýšit výkon nejprve vytvoří <xref:System.Data.DataView> pro **DataTable**. Vytváření **DataView** indexuje řádky tabulky. **Vyberte** metoda pak usees, které indexu, výrazně snižuje čas potřebný k vygenerování výsledku dotazu. Informace o vytváření **DataView** pro **DataTable**, najdete v části [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
 **Vyberte** metoda určuje, která verze řádky, které umožňuje zobrazit nebo upravit na základě <xref:System.Data.DataViewRowState>. Následující tabulka popisuje možné **DataViewRowState** hodnot výčtu.  
  
|Hodnota DataViewRowState|Popis|  
|----------------------------|-----------------|  
|**CurrentRows**|Aktuální řádky včetně beze změny, přidání a změny řádků.|  
|**Odstranit**|Odstraněné řádek.|  
|**ModifiedCurrent**|Aktuální verze, která je upravenou verzi původního data. (Viz **ModifiedOriginal**.)|  
|**ModifiedOriginal**|Původní verze všechny změny řádky. Aktuální verze je k dispozici pomocí **ModifiedCurrent**.|  
|**Přidat**|Nový řádek.|  
|**None**|Žádné|  
|**OriginalRows**|Původní řádky, včetně beze změny a odstranit řádky.|  
|**Beze změny**|Beze změny řádků.|  
  
 V následujícím příkladu **datovou sadu** objektu je filtrované tak, že pouze pracujete s řádky jehož **DataViewRowState** je nastaven na **CurrentRows**.  
  
```vb  
Dim column As DataColumn  
Dim row As DataRow  
  
Dim currentRows() As DataRow = _  
    workTable.Select(Nothing, Nothing, DataViewRowState.CurrentRows)  
  
If (currentRows.Length < 1 ) Then  
  Console.WriteLine("No Current Rows Found")  
Else  
  For Each column in workTable.Columns  
    Console.Write(vbTab & column.ColumnName)  
  Next  
  
  Console.WriteLine(vbTab & "RowState")  
  
  For Each row In currentRows  
    For Each column In workTable.Columns  
      Console.Write(vbTab & row(column).ToString())  
    Next  
  
    Dim rowState As String = _  
        System.Enum.GetName(row.RowState.GetType(), row.RowState)  
    Console.WriteLine(vbTab & rowState)  
  Next  
End If  
```  
  
```csharp  
DataRow[] currentRows = workTable.Select(  
    null, null, DataViewRowState.CurrentRows);  
  
if (currentRows.Length < 1 )  
  Console.WriteLine("No Current Rows Found");  
else  
{  
  foreach (DataColumn column in workTable.Columns)  
    Console.Write("\t{0}", column.ColumnName);  
  
  Console.WriteLine("\tRowState");  
  
  foreach (DataRow row in currentRows)  
  {  
    foreach (DataColumn column in workTable.Columns)  
      Console.Write("\t{0}", row[column]);  
  
    Console.WriteLine("\t" + row.RowState);  
  }  
}  
```  
  
 **Vyberte** metoda slouží k vrátí řádky s různými **RowState** hodnoty nebo hodnoty polí. Následující příklad vrací **DataRow** pole, která odkazuje na všechny řádky, které byly odstraněny a vrátí jiné **DataRow** pole, která odkazuje na všechny řádky, seřazené podle **CustLName**, kde **CustID** sloupec je větší než 5. Informace o tom, jak zobrazit informace v **odstraněné** řádek najdete v tématu [stavy řádků a verze řádku](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
```vb  
' Retrieve all deleted rows.  
Dim deletedRows() As DataRow = workTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
' Retrieve rows where CustID > 5, and order by CustLName.  
Dim custRows() As DataRow = workTable.Select( _  
    "CustID > 5", "CustLName ASC")  
```  
  
```csharp  
// Retrieve all deleted rows.  
DataRow[] deletedRows = workTable.Select(  
    null, null, DataViewRowState.Deleted);  
  
// Retrieve rows where CustID > 5, and order by CustLName.  
DataRow[] custRows = workTable.Select("CustID > 5", "CustLName ASC");  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataViewRowState>  
 [Manipulace s daty v datové tabulce](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [Stavy řádků a verze řádků](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
