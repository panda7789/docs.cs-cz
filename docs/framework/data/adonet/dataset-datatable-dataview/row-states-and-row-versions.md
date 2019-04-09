---
title: Stavy řádků a verze řádků
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 83147c3f9d70434f5c8dd34e2e56f44f71adc53d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092900"
---
# <a name="row-states-and-row-versions"></a>Stavy řádků a verze řádků
ADO.NET spravuje řádků v tabulkách stavy řádků a verze. Stav řádek znamená stavový řádek; verze řádků Udržovat hodnoty uložené v řádku, jako jsou změny, včetně aktuální a původní, výchozí hodnoty. Například po provedení změny na sloupec v řádku, řádku budou mít stav řádku `Modified`, a dvě verze řádků: `Current`, který obsahuje hodnoty aktuálního řádku a `Original`, obsahující hodnoty řádků dříve, než byl sloupec upravit.  
  
 Každý <xref:System.Data.DataRow> má objekt <xref:System.Data.DataRow.RowState%2A> vlastnost, která můžete zkoumat, chcete-li zjistit aktuální stav řádku. Následující tabulka obsahuje stručný popis jednotlivých `RowState` hodnota výčtu.  
  
|Hodnota RowState|Popis|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|Byly provedeny žádné změny od posledního volání `AcceptChanges` nebo od řádku vytvořil `DataAdapter.Fill`.|  
|<xref:System.Data.DataRowState.Added>|Řádek byl přidán do tabulky, ale `AcceptChanges` se nevolala.|  
|<xref:System.Data.DataRowState.Modified>|Některé prvek řádku byl změněn.|  
|<xref:System.Data.DataRowState.Deleted>|Na řádku byla odstraněna z tabulky, a `AcceptChanges` se nevolala.|  
|<xref:System.Data.DataRowState.Detached>|Řádek není součástí žádné `DataRowCollection`. `RowState` Nově vytvořený řádku je nastavena na `Detached`. Po nové `DataRow` se přidá do `DataRowCollection` voláním `Add` metoda, hodnota `RowState` je nastavena na `Added`.<br /><br /> `Detached` je také nastavena pro řádek, který byl odebrán z `DataRowCollection` pomocí `Remove` metodu, nebo `Delete` následuje metoda `AcceptChanges` – metoda.|  
  
 Když `AcceptChanges` je volán na <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , nebo <xref:System.Data.DataRow>, všechny řádky se stavem řádek `Deleted` se odeberou. Zbývající řádky jsou uvedeny ve stavu řádku `Unchanged`a hodnotami ve `Original` jsou přepsány verze řádku `Current` řádek hodnoty verze. Když `RejectChanges` nazývá všechny řádky se stavem řádek `Added` se odeberou. Zbývající řádky jsou uvedeny ve stavu řádku `Unchanged`a hodnotami ve `Current` jsou přepsány verze řádku `Original` řádek hodnoty verze.  
  
 Verze odlišný řádek řádku můžete zobrazit pomocí předání <xref:System.Data.DataRowVersion> parametr odkazem na sloupec, jak je znázorněno v následujícím příkladu.  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 Následující tabulka obsahuje stručný popis jednotlivých `DataRowVersion` hodnota výčtu.  
  
|Hodnota DataRowVersion|Popis|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|Aktuální hodnoty řádku. Tato verze řádků pro řádky s neexistuje `RowState` z `Deleted`.|  
|<xref:System.Data.DataRowVersion.Default>|Výchozí verze řádků pro konkrétní řádek. Výchozí verze řádků pro `Added`, `Modified`, nebo `Deleted` řádek je `Current`. Výchozí verze řádků pro `Detached` řádek je `Proposed`.|  
|<xref:System.Data.DataRowVersion.Original>|Původní hodnoty řádku. Tato verze řádků pro řádky s neexistuje `RowState` z `Added`.|  
|<xref:System.Data.DataRowVersion.Proposed>|Navrhované hodnoty řádku. Tato verze řádku existuje během operace úpravy na řádku, nebo pro řádek, který není součástí `DataRowCollection`.|  
  
 Můžete otestovat, jestli `DataRow` má verzi konkrétního řádku voláním <xref:System.Data.DataRow.HasVersion%2A> metoda a předávání `DataRowVersion` jako argument. Například `DataRow.HasVersion(DataRowVersion.Original)` vrátí `false` pro nově přidané řádky před `AcceptChanges` byla volána.  
  
 Následující příklad kódu zobrazuje hodnoty v odstraněné řádky tabulky. `Deleted` není nutné řádků `Current` verze řádku, takže je nutné předat `DataRowVersion.Original` při přístupu k hodnot sloupců.  
  
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

- [Manipulace s daty v datové tabulce](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Adaptéry a čtečky dat](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
