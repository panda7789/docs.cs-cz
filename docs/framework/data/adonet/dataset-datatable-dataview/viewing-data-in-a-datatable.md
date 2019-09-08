---
title: Zobrazení dat v datové tabulce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: c13f0b802b2714a17ea4014625a65ebd1b0011f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785848"
---
# <a name="viewing-data-in-a-datatable"></a>Zobrazení dat v datové tabulce

K <xref:System.Data.DataTable> obsahu můžete přistupovat pomocí kolekcí **řádky** a **sloupce** **objektu DataTable**. Můžete také použít <xref:System.Data.DataTable.Select%2A> metodu pro vrácení podmnožiny dat v **objektu DataTable** podle kritérií, včetně kritérií hledání, pořadí řazení a stavu řádku. Kromě toho můžete použít <xref:System.Data.DataRowCollection.Find%2A> metodu **kolekci DataRowCollection** při hledání konkrétního řádku pomocí hodnoty primárního klíče.

Metoda **Select** objektu **DataTable** vrací sadu <xref:System.Data.DataRow> objektů, které odpovídají zadaným kritériím. **Vyberte možnost** přebírá volitelné argumenty výrazu filtru, výraz řazení a **DataViewRowState**. Výraz filtru určuje, které řádky se mají vrátit na základě hodnot **DataColumn** , například `LastName = 'Smith'`. Výraz řazení se řídí standardními konvencemi SQL pro řazení sloupců, `LastName ASC, FirstName ASC`například. Pravidla týkající se psaní výrazů naleznete v tématu <xref:System.Data.DataColumn.Expression%2A> vlastnost třídy **DataColumn** .

> [!TIP]
> Provádíte-li několik volání metody **Select** **objektu DataTable**, lze zvýšit výkon tím, že <xref:System.Data.DataView> nejprve vytvoříte objekt pro **DataTable**. Vytvořením objektu **DataView** se naindexuje řádky tabulky. Metoda **Select** pak použije tento index, což významně zkracuje čas k vygenerování výsledku dotazu. Informace o vytvoření objektu **DataView** pro **objekt DataTable**naleznete v tématu [DataViews](dataviews.md).

Metoda **Select** určuje, která verze řádků se má zobrazit nebo manipulovat na základě <xref:System.Data.DataViewRowState>. Následující tabulka popisuje možné hodnoty výčtu **DataViewRowState** .

|Hodnota DataViewRowState|Popis|
|----------------------------|-----------------|
|**CurrentRows**|Aktuální řádky, včetně nezměněných, přidaných a upravených řádků.|
|**Odstraňování**|Odstraněný řádek.|
|**ModifiedCurrent**|Aktuální verze, která je upravená verze původních dat. (Viz **ModifiedOriginal**.)|
|**ModifiedOriginal**|Původní verze všech upravených řádků. Aktuální verze je k dispozici pomocí **ModifiedCurrent**.|
|**Přidat**|Nový řádek.|
|**Žádné**|Žádné|
|**OriginalRows**|Původní řádky, včetně nezměněných a odstraněných řádků.|
|**Oproti**|Nezměněný řádek.|

V následujícím příkladu je objekt **DataSet** filtrován, takže pracujete pouze s řádky, jejichž **DataViewRowState** je nastaven na **CurrentRows**.

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

Metodu **Select** lze použít k vrácení řádků s různými hodnotami **RowState** nebo hodnotami polí. Následující příklad vrátí pole **DataRow** , které odkazuje na všechny řádky, které byly odstraněny, a vrátí další pole **DataRow** , které odkazuje na všechny řádky seřazené podle **CustLName**, kde sloupec **custid** je větší než 5. Informace o tom, jak zobrazit informace na **odstraněném** řádku, najdete v tématu [stavy řádků a verze řádků](row-states-and-row-versions.md).

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

## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataViewRowState>
- [Manipulace s daty v datové tabulce](manipulating-data-in-a-datatable.md)
- [Stavy řádků a verze řádků](row-states-and-row-versions.md)
- [Přehled ADO.NET](../ado-net-overview.md)
