---
title: Zobrazení dat v datové tabulce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: de745633060dd4f7b1610492d0ff57ec7a4f545b
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2018
ms.locfileid: "46710706"
---
# <a name="viewing-data-in-a-datatable"></a>Zobrazení dat v datové tabulce
Můžete přístup k obsahu <xref:System.Data.DataTable> pomocí **řádky** a **sloupce** kolekce **DataTable**. Můžete také použít <xref:System.Data.DataTable.Select%2A> metoda vrátí podmnožiny dat v **DataTable** podle kritérií kritéria vyhledávání, řazení a řádek stavu. Kromě toho můžete použít <xref:System.Data.DataRowCollection.Find%2A> metodu **kolekci DataRowCollection** při hledání konkrétního řádku pomocí hodnoty primárního klíče.  
  
 **Vyberte** metodu **DataTable** objekt vrací sadu <xref:System.Data.DataRow> objekty, které odpovídají zadaným kritériím. **Vyberte** přebírá nepovinné argumenty výrazu filtru, řadicí výraz, a **DataViewRowState**. Výraz filtru identifikuje řádky, které chcete vrátit na základě **DataColumn** hodnoty, jako například `LastName = 'Smith'`. Výraz řazení dodržuje standardní konvence SQL pro řazení sloupců, třeba `LastName ASC, FirstName ASC`. Pravidla týkající se vytváření výrazů, najdete v článku <xref:System.Data.DataColumn.Expression%2A> vlastnost **DataColumn** třídy.  
  
> [!TIP]
>  Pokud provádíte počet volání **vyberte** metodu **DataTable**, může zvýšit výkon tím, že vytvoříte první <xref:System.Data.DataView> pro **DataTable**. Vytváří **DataView** indexuje řádky tabulky. **Vyberte** metoda pak usees, které indexu, což výrazně zkrátí čas k vygenerování výsledku dotazu. Informace o vytváření **DataView** pro **DataTable**, naleznete v tématu [zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
 **Vyberte** metoda určí na základě verze řádků, které chcete zobrazit nebo pracovat <xref:System.Data.DataViewRowState>. Následující tabulka popisuje možné **DataViewRowState** hodnot výčtu.  
  
|Hodnota DataViewRowState|Popis|  
|----------------------------|-----------------|  
|**CurrentRows**|Aktuální řádky včetně beze změny, přidání a upravené řádky.|  
|**Odstranit**|Odstraněný řádek.|  
|**ModifiedCurrent**|Aktuální verzi, která je upravená verze původní data. (Viz **ModifiedOriginal**.)|  
|**ModifiedOriginal**|Původní verzi všechny změněné řádky. Aktuální verze je k dispozici pomocí **ModifiedCurrent**.|  
|**Přidat**|Nový řádek.|  
|**None**|Žádné|  
|**OriginalRows**|Původní řádky, včetně beze změny a odstranit řádky.|  
|**beze změny**|Beze změny řádků.|  
  
 V následujícím příkladu **datovou sadu** objektu je filtrována tak, aby pouze pracujete s řádky jehož **DataViewRowState** je nastavena na **CurrentRows**.  
  
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
  
 **Vyberte** metodu je možné vrátit řádky s různými **RowState** hodnoty nebo hodnot polí. Následující příklad vrátí **DataRow** pole, které odkazuje na všechny řádky, které se odstranily a vrátí jiný **DataRow** pole, které odkazuje na všechny řádky, seřazené podle **CustLName**, kde **CustID** sloupec je větší než 5. Informace o tom, jak zobrazit informace v **odstraněné** řádek, přečtěte si téma [stavy řádků a verze řádků](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
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
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
