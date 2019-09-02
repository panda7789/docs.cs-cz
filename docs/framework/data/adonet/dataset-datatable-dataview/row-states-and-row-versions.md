---
title: Stavy řádků a verze řádků
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 24d0d44f5964708164f89b0d9fa6c4c1aac7da0b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204504"
---
# <a name="row-states-and-row-versions"></a>Stavy řádků a verze řádků
ADO.NET spravuje řádky v tabulkách pomocí stavů a verzí řádků. Stav řádku určuje stav řádku; verze řádků udržují hodnoty uložené v řádku beze změny, včetně aktuálních, původních a výchozích hodnot. Například po provedení úprav sloupce v řádku bude mít řádek stav `Modified`řádku a dvě verze řádku: `Current`, který obsahuje hodnoty aktuálního řádku, a `Original`, který obsahuje hodnoty řádků před tím, než byl sloupec změn.  
  
 Každý <xref:System.Data.DataRow> objekt<xref:System.Data.DataRow.RowState%2A> má vlastnost, kterou můžete prozkoumávat, abyste určili aktuální stav řádku. Následující tabulka obsahuje stručný popis každé `RowState` hodnoty výčtu.  
  
|Hodnota RowState|Popis|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|Od posledního volání do `AcceptChanges` nebo od chvíle, kdy byl řádek vytvořen pomocí `DataAdapter.Fill`, nebyly provedeny žádné změny.|  
|<xref:System.Data.DataRowState.Added>|Řádek byl přidán do tabulky, ale `AcceptChanges` nebyl volán.|  
|<xref:System.Data.DataRowState.Modified>|Byl změněn nějaký element řádku.|  
|<xref:System.Data.DataRowState.Deleted>|Řádek byl odstraněn z tabulky a `AcceptChanges` nebyl volán.|  
|<xref:System.Data.DataRowState.Detached>|Řádek není součástí žádného `DataRowCollection`řádku. Nově vytvořený řádek je nastaven na `Detached`hodnotu. `RowState` Po přidání nového `DataRow` do rozhraní `DataRowCollection` voláním `Add` metody je hodnota `RowState` vlastnosti nastavena na `Added`.<br /><br /> `Detached`je také nastaveno pro řádek, `DataRowCollection` který byl odebrán z `Remove` `Delete` metody pomocí metody, nebo metodou následovanou `AcceptChanges` metodou.|  
  
 Když `AcceptChanges` je volána <xref:System.Data.DataSet>na, <xref:System.Data.DataTable> `Deleted` nebo <xref:System.Data.DataRow>, jsou odebrány všechny řádky se stavem řádku. Zbývajícím řádkům je uveden stav `Unchanged`řádku a hodnoty `Original` ve verzi řádku `Current` jsou přepsány hodnotami verze řádku. Při `RejectChanges` volání se odeberou všechny řádky se `Added` stavem řádku. Zbývajícím řádkům je uveden stav `Unchanged`řádku a hodnoty `Current` ve verzi řádku `Original` jsou přepsány hodnotami verze řádku.  
  
 Můžete zobrazit různé verze řádku předáním <xref:System.Data.DataRowVersion> parametru s odkazem na sloupec, jak je znázorněno v následujícím příkladu.  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 Následující tabulka obsahuje stručný popis každé `DataRowVersion` hodnoty výčtu.  
  
|Hodnota DataRowVersion|Popis|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|Aktuální hodnoty pro řádek Tato verze řádku neexistuje pro řádky s `RowState`. `Deleted`|  
|<xref:System.Data.DataRowVersion.Default>|Výchozí verze řádku pro určitý řádek Výchozí verze řádku `Added`pro, `Modified`nebo `Deleted` je `Current`. Výchozí verze řádku pro `Detached` řádek je. `Proposed`|  
|<xref:System.Data.DataRowVersion.Original>|Původní hodnoty pro řádek Tato verze řádku neexistuje pro řádky s `RowState`. `Added`|  
|<xref:System.Data.DataRowVersion.Proposed>|Navrhované hodnoty pro řádek Tato verze řádku existuje během operace Edit na řádku nebo pro řádek, který není součástí `DataRowCollection`.|  
  
 Můžete otestovat, zda `DataRow` má konkrétní verzi řádku <xref:System.Data.DataRow.HasVersion%2A> voláním metody a předáním `DataRowVersion` jako argumentu. Například `DataRow.HasVersion(DataRowVersion.Original)` `AcceptChanges` vrátí `false` pro nově přidané řádky před voláním.  
  
 Následující příklad kódu zobrazuje hodnoty ze všech odstraněných řádků v tabulce. `Deleted`řádky nemají verzi `DataRowVersion.Original` řádku,takžejenutnépřipřístupukhodnotám`Current` sloupců předat.  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
  
Dim delRows() As DataRow = catTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
Console.WriteLine("Deleted rows:" & vbCrLf)  
  
Dim catCol As DataColumn  
Dim delRow As DataRow  
  
For Each catCol In catTable.Columns  
  Console.Write(catCol.ColumnName & vbTab)  
Next  
Console.WriteLine()  
  
For Each delRow In delRows  
  For Each catCol In catTable.Columns  
    Console.Write(delRow(catCol, DataRowVersion.Original) & vbTab)  
  Next  
  Console.WriteLine()  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
  
DataRow[] delRows = catTable.Select(null, null, DataViewRowState.Deleted);  
  
Console.WriteLine("Deleted rows:\n");  
  
foreach (DataColumn catCol in catTable.Columns)  
  Console.Write(catCol.ColumnName + "\t");  
Console.WriteLine();  
  
foreach (DataRow delRow in delRows)  
{  
  foreach (DataColumn catCol in catTable.Columns)  
    Console.Write(delRow[catCol, DataRowVersion.Original] + "\t");  
  Console.WriteLine();  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [Manipulace s daty v datové tabulce](manipulating-data-in-a-datatable.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Adaptéry a čtečky dat](../dataadapters-and-datareaders.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
