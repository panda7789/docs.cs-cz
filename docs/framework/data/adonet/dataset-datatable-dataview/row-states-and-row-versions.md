---
title: "Stavy řádků a verze řádku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f03ddd0c8a09826068ae30e23773016faf3f56e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="row-states-and-row-versions"></a>Stavy řádků a verze řádku
ADO.NET spravuje řádků v tabulkách pomocí stavy řádků a verze. Stav řádek označuje stav řádku. verze řádku udržovat hodnotami uloženými v řádku, jako je upravená, včetně aktuální a původní, výchozí hodnoty. Například po provedení změny na sloupec v řádku, řádku bude mít řádek stavu `Modified`, a dvě verze řádku: `Current`, která obsahuje aktuální hodnoty řádků a `Original`, obsahující hodnoty řádků před sloupci upravit.  
  
 Každý <xref:System.Data.DataRow> objekt má <xref:System.Data.DataRow.RowState%2A> vlastnost, která můžete prozkoumat k určení aktuální stav řádku. Následující tabulka obsahuje stručný popis jednotlivých `RowState` hodnota výčtu.  
  
|Hodnota RowState|Popis|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|Nebyly provedeny žádné změny od posledního volání `AcceptChanges` nebo vzhledem k tomu, že byl vytvořen řádek `DataAdapter.Fill`.|  
|<xref:System.Data.DataRowState.Added>|Řádek je přidaný do tabulky, ale `AcceptChanges` nebyla volána.|  
|<xref:System.Data.DataRowState.Modified>|Některé element řádek byl změněn.|  
|<xref:System.Data.DataRowState.Deleted>|Řádek odstraněný z tabulky, a `AcceptChanges` nebyla volána.|  
|<xref:System.Data.DataRowState.Detached>|Řádek není součástí žádné `DataRowCollection`. `RowState` Nově vytvořený řádku je nastaven na `Detached`. Po nové `DataRow` je přidán do `DataRowCollection` voláním `Add` metoda, hodnota `RowState` je nastavena na `Added`.<br /><br /> `Detached`nastavený i pro řádek, který byl odebrán z `DataRowCollection` pomocí `Remove` metoda, nebo `Delete` metoda následuje `AcceptChanges` metoda.|  
  
 Když `AcceptChanges` se volá na <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , nebo <xref:System.Data.DataRow>, všechny řádky se stavem řádek `Deleted` se odeberou. Zbývající řádky jsou uvedeny stavu řádek `Unchanged`a hodnotami ve `Original` verze řádku jsou přepsána `Current` řádek hodnoty verze. Když `RejectChanges` je volána, všechny řádky se stavem řádek `Added` se odeberou. Zbývající řádky jsou uvedeny stavu řádek `Unchanged`a hodnotami ve `Current` verze řádku jsou přepsána `Original` řádek hodnoty verze.  
  
 Jiný řádek verze řádku můžete zobrazit pomocí předání <xref:System.Data.DataRowVersion> parametr s odkaz na sloupec, jak je znázorněno v následujícím příkladu.  
  
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
|<xref:System.Data.DataRowVersion.Current>|Aktuální hodnoty pro řádek. Tato verze řádku pro řádky s neexistuje `RowState` z `Deleted`.|  
|<xref:System.Data.DataRowVersion.Default>|Řádek je výchozí verze pro konkrétního řádku. Výchozí verze řádku pro `Added`, `Modified`, nebo `Unchanged` řádek je `Current`. Výchozí řádek verze pro `Deleted` řádek je `Original`. Výchozí řádek verze pro `Detached` řádek je `Proposed`.|  
|<xref:System.Data.DataRowVersion.Original>|Původní hodnoty pro řádek. Tato verze řádku pro řádky s neexistuje `RowState` z `Added`.|  
|<xref:System.Data.DataRowVersion.Proposed>|Navrhované hodnoty pro řádek. Tato verze řádku existuje během operace upravit na řádek nebo pro řádek, který není součástí `DataRowCollection`.|  
  
 Můžete otestovat, zda `DataRow` má verzi konkrétního řádku voláním <xref:System.Data.DataRow.HasVersion%2A> metoda a předávání `DataRowVersion` jako argument. Například `DataRow.HasVersion(DataRowVersion.Original)` vrátí `false` pro nově přidaného řádky před `AcceptChanges` byla volána.  
  
 Následující příklad kódu zobrazuje hodnoty v všechny odstraněné řádky tabulky. `Deleted`řádky nemají `Current` verze řádku, takže je nutné předat `DataRowVersion.Original` při přístupu k hodnoty ve sloupcích.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Manipulace s daty v DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [Datové sady, DataTables a DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [DataAdapters a DataReaders](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
