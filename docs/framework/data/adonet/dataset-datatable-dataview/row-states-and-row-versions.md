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
# <a name="row-states-and-row-versions"></a><span data-ttu-id="d7284-102">Stavy řádků a verze řádku</span><span class="sxs-lookup"><span data-stu-id="d7284-102">Row States and Row Versions</span></span>
<span data-ttu-id="d7284-103">ADO.NET spravuje řádků v tabulkách pomocí stavy řádků a verze.</span><span class="sxs-lookup"><span data-stu-id="d7284-103">ADO.NET manages rows in tables using row states and versions.</span></span> <span data-ttu-id="d7284-104">Stav řádek označuje stav řádku. verze řádku udržovat hodnotami uloženými v řádku, jako je upravená, včetně aktuální a původní, výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d7284-104">A row state indicates the status of a row; row versions maintain the values stored in a row as it is modified, including current, original, and default values.</span></span> <span data-ttu-id="d7284-105">Například po provedení změny na sloupec v řádku, řádku bude mít řádek stavu `Modified`, a dvě verze řádku: `Current`, která obsahuje aktuální hodnoty řádků a `Original`, obsahující hodnoty řádků před sloupci upravit.</span><span class="sxs-lookup"><span data-stu-id="d7284-105">For example, after you have made a modification to a column in a row, the row will have a row state of `Modified`, and two row versions: `Current`, which contains the current row values, and `Original`, which contains the row values before the column was modified.</span></span>  
  
 <span data-ttu-id="d7284-106">Každý <xref:System.Data.DataRow> objekt má <xref:System.Data.DataRow.RowState%2A> vlastnost, která můžete prozkoumat k určení aktuální stav řádku.</span><span class="sxs-lookup"><span data-stu-id="d7284-106">Each <xref:System.Data.DataRow> object has a <xref:System.Data.DataRow.RowState%2A> property that you can examine to determine the current state of the row.</span></span> <span data-ttu-id="d7284-107">Následující tabulka obsahuje stručný popis jednotlivých `RowState` hodnota výčtu.</span><span class="sxs-lookup"><span data-stu-id="d7284-107">The following table gives a brief description of each `RowState` enumeration value.</span></span>  
  
|<span data-ttu-id="d7284-108">Hodnota RowState</span><span class="sxs-lookup"><span data-stu-id="d7284-108">RowState value</span></span>|<span data-ttu-id="d7284-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d7284-109">Description</span></span>|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|<span data-ttu-id="d7284-110">Nebyly provedeny žádné změny od posledního volání `AcceptChanges` nebo vzhledem k tomu, že byl vytvořen řádek `DataAdapter.Fill`.</span><span class="sxs-lookup"><span data-stu-id="d7284-110">No changes have been made since the last call to `AcceptChanges` or since the row was created by `DataAdapter.Fill`.</span></span>|  
|<xref:System.Data.DataRowState.Added>|<span data-ttu-id="d7284-111">Řádek je přidaný do tabulky, ale `AcceptChanges` nebyla volána.</span><span class="sxs-lookup"><span data-stu-id="d7284-111">The row has been added to the table, but `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Modified>|<span data-ttu-id="d7284-112">Některé element řádek byl změněn.</span><span class="sxs-lookup"><span data-stu-id="d7284-112">Some element of the row has been changed.</span></span>|  
|<xref:System.Data.DataRowState.Deleted>|<span data-ttu-id="d7284-113">Řádek odstraněný z tabulky, a `AcceptChanges` nebyla volána.</span><span class="sxs-lookup"><span data-stu-id="d7284-113">The row has been deleted from a table, and `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Detached>|<span data-ttu-id="d7284-114">Řádek není součástí žádné `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="d7284-114">The row is not part of any `DataRowCollection`.</span></span> <span data-ttu-id="d7284-115">`RowState` Nově vytvořený řádku je nastaven na `Detached`.</span><span class="sxs-lookup"><span data-stu-id="d7284-115">The `RowState` of a newly created row is set to `Detached`.</span></span> <span data-ttu-id="d7284-116">Po nové `DataRow` je přidán do `DataRowCollection` voláním `Add` metoda, hodnota `RowState` je nastavena na `Added`.</span><span class="sxs-lookup"><span data-stu-id="d7284-116">After the new `DataRow` is added to the `DataRowCollection` by calling the `Add` method, the value of the `RowState` property is set to `Added`.</span></span><br /><br /> <span data-ttu-id="d7284-117">`Detached`nastavený i pro řádek, který byl odebrán z `DataRowCollection` pomocí `Remove` metoda, nebo `Delete` metoda následuje `AcceptChanges` metoda.</span><span class="sxs-lookup"><span data-stu-id="d7284-117">`Detached` is also set for a row that has been removed from a `DataRowCollection` using the `Remove` method, or by the `Delete` method followed by the `AcceptChanges` method.</span></span>|  
  
 <span data-ttu-id="d7284-118">Když `AcceptChanges` se volá na <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , nebo <xref:System.Data.DataRow>, všechny řádky se stavem řádek `Deleted` se odeberou.</span><span class="sxs-lookup"><span data-stu-id="d7284-118">When `AcceptChanges` is called on a <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , or <xref:System.Data.DataRow>, all rows with a row state of `Deleted` are removed.</span></span> <span data-ttu-id="d7284-119">Zbývající řádky jsou uvedeny stavu řádek `Unchanged`a hodnotami ve `Original` verze řádku jsou přepsána `Current` řádek hodnoty verze.</span><span class="sxs-lookup"><span data-stu-id="d7284-119">The remaining rows are given a row state of `Unchanged`, and the values in the `Original` row version are overwritten with the `Current` row version values.</span></span> <span data-ttu-id="d7284-120">Když `RejectChanges` je volána, všechny řádky se stavem řádek `Added` se odeberou.</span><span class="sxs-lookup"><span data-stu-id="d7284-120">When `RejectChanges` is called, all rows with a row state of `Added` are removed.</span></span> <span data-ttu-id="d7284-121">Zbývající řádky jsou uvedeny stavu řádek `Unchanged`a hodnotami ve `Current` verze řádku jsou přepsána `Original` řádek hodnoty verze.</span><span class="sxs-lookup"><span data-stu-id="d7284-121">The remaining rows are given a row state of `Unchanged`, and the values in the `Current` row version are overwritten with the `Original` row version values.</span></span>  
  
 <span data-ttu-id="d7284-122">Jiný řádek verze řádku můžete zobrazit pomocí předání <xref:System.Data.DataRowVersion> parametr s odkaz na sloupec, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d7284-122">You can view the different row versions of a row by passing a <xref:System.Data.DataRowVersion> parameter with the column reference, as shown in the following example.</span></span>  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 <span data-ttu-id="d7284-123">Následující tabulka obsahuje stručný popis jednotlivých `DataRowVersion` hodnota výčtu.</span><span class="sxs-lookup"><span data-stu-id="d7284-123">The following table gives a brief description of each `DataRowVersion` enumeration value.</span></span>  
  
|<span data-ttu-id="d7284-124">Hodnota DataRowVersion</span><span class="sxs-lookup"><span data-stu-id="d7284-124">DataRowVersion value</span></span>|<span data-ttu-id="d7284-125">Popis</span><span class="sxs-lookup"><span data-stu-id="d7284-125">Description</span></span>|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|<span data-ttu-id="d7284-126">Aktuální hodnoty pro řádek.</span><span class="sxs-lookup"><span data-stu-id="d7284-126">The current values for the row.</span></span> <span data-ttu-id="d7284-127">Tato verze řádku pro řádky s neexistuje `RowState` z `Deleted`.</span><span class="sxs-lookup"><span data-stu-id="d7284-127">This row version does not exist for rows with a `RowState` of `Deleted`.</span></span>|  
|<xref:System.Data.DataRowVersion.Default>|<span data-ttu-id="d7284-128">Řádek je výchozí verze pro konkrétního řádku.</span><span class="sxs-lookup"><span data-stu-id="d7284-128">The default row version for a particular row.</span></span> <span data-ttu-id="d7284-129">Výchozí verze řádku pro `Added`, `Modified`, nebo `Unchanged` řádek je `Current`.</span><span class="sxs-lookup"><span data-stu-id="d7284-129">The default row version for an `Added`, `Modified`, or `Unchanged` row is `Current`.</span></span> <span data-ttu-id="d7284-130">Výchozí řádek verze pro `Deleted` řádek je `Original`.</span><span class="sxs-lookup"><span data-stu-id="d7284-130">The default row version for a `Deleted` row is `Original`.</span></span> <span data-ttu-id="d7284-131">Výchozí řádek verze pro `Detached` řádek je `Proposed`.</span><span class="sxs-lookup"><span data-stu-id="d7284-131">The default row version for a `Detached` row is `Proposed`.</span></span>|  
|<xref:System.Data.DataRowVersion.Original>|<span data-ttu-id="d7284-132">Původní hodnoty pro řádek.</span><span class="sxs-lookup"><span data-stu-id="d7284-132">The original values for the row.</span></span> <span data-ttu-id="d7284-133">Tato verze řádku pro řádky s neexistuje `RowState` z `Added`.</span><span class="sxs-lookup"><span data-stu-id="d7284-133">This row version does not exist for rows with a `RowState` of `Added`.</span></span>|  
|<xref:System.Data.DataRowVersion.Proposed>|<span data-ttu-id="d7284-134">Navrhované hodnoty pro řádek.</span><span class="sxs-lookup"><span data-stu-id="d7284-134">The proposed values for the row.</span></span> <span data-ttu-id="d7284-135">Tato verze řádku existuje během operace upravit na řádek nebo pro řádek, který není součástí `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="d7284-135">This row version exists during an edit operation on a row, or for a row that is not part of a `DataRowCollection`.</span></span>|  
  
 <span data-ttu-id="d7284-136">Můžete otestovat, zda `DataRow` má verzi konkrétního řádku voláním <xref:System.Data.DataRow.HasVersion%2A> metoda a předávání `DataRowVersion` jako argument.</span><span class="sxs-lookup"><span data-stu-id="d7284-136">You can test whether a `DataRow` has a particular row version by calling the <xref:System.Data.DataRow.HasVersion%2A> method and passing a `DataRowVersion` as an argument.</span></span> <span data-ttu-id="d7284-137">Například `DataRow.HasVersion(DataRowVersion.Original)` vrátí `false` pro nově přidaného řádky před `AcceptChanges` byla volána.</span><span class="sxs-lookup"><span data-stu-id="d7284-137">For example, `DataRow.HasVersion(DataRowVersion.Original)` will return `false` for newly added rows before `AcceptChanges` has been called.</span></span>  
  
 <span data-ttu-id="d7284-138">Následující příklad kódu zobrazuje hodnoty v všechny odstraněné řádky tabulky.</span><span class="sxs-lookup"><span data-stu-id="d7284-138">The following code example displays the values in all the deleted rows of a table.</span></span> <span data-ttu-id="d7284-139">`Deleted`řádky nemají `Current` verze řádku, takže je nutné předat `DataRowVersion.Original` při přístupu k hodnoty ve sloupcích.</span><span class="sxs-lookup"><span data-stu-id="d7284-139">`Deleted` rows do not have a `Current` row version, so you must pass `DataRowVersion.Original` when accessing the column values.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d7284-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7284-140">See Also</span></span>  
 [<span data-ttu-id="d7284-141">Manipulace s daty v DataTable</span><span class="sxs-lookup"><span data-stu-id="d7284-141">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="d7284-142">Datové sady, DataTables a DataView</span><span class="sxs-lookup"><span data-stu-id="d7284-142">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="d7284-143">DataAdapters a DataReaders</span><span class="sxs-lookup"><span data-stu-id="d7284-143">DataAdapters and DataReaders</span></span>](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="d7284-144">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="d7284-144">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
