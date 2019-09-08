---
title: Stavy řádků a verze řádků
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 70596d6acb62fa01092e5e55dd3b6c84eb162b5d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784339"
---
# <a name="row-states-and-row-versions"></a><span data-ttu-id="a816b-102">Stavy řádků a verze řádků</span><span class="sxs-lookup"><span data-stu-id="a816b-102">Row States and Row Versions</span></span>
<span data-ttu-id="a816b-103">ADO.NET spravuje řádky v tabulkách pomocí stavů a verzí řádků.</span><span class="sxs-lookup"><span data-stu-id="a816b-103">ADO.NET manages rows in tables using row states and versions.</span></span> <span data-ttu-id="a816b-104">Stav řádku určuje stav řádku; verze řádků udržují hodnoty uložené v řádku beze změny, včetně aktuálních, původních a výchozích hodnot.</span><span class="sxs-lookup"><span data-stu-id="a816b-104">A row state indicates the status of a row; row versions maintain the values stored in a row as it is modified, including current, original, and default values.</span></span> <span data-ttu-id="a816b-105">Například po provedení úprav sloupce v řádku bude mít řádek stav `Modified`řádku a dvě verze řádku: `Current`, který obsahuje hodnoty aktuálního řádku, a `Original`, který obsahuje hodnoty řádků před tím, než byl sloupec změn.</span><span class="sxs-lookup"><span data-stu-id="a816b-105">For example, after you have made a modification to a column in a row, the row will have a row state of `Modified`, and two row versions: `Current`, which contains the current row values, and `Original`, which contains the row values before the column was modified.</span></span>  
  
 <span data-ttu-id="a816b-106">Každý <xref:System.Data.DataRow> objekt<xref:System.Data.DataRow.RowState%2A> má vlastnost, kterou můžete prozkoumávat, abyste určili aktuální stav řádku.</span><span class="sxs-lookup"><span data-stu-id="a816b-106">Each <xref:System.Data.DataRow> object has a <xref:System.Data.DataRow.RowState%2A> property that you can examine to determine the current state of the row.</span></span> <span data-ttu-id="a816b-107">Následující tabulka obsahuje stručný popis každé `RowState` hodnoty výčtu.</span><span class="sxs-lookup"><span data-stu-id="a816b-107">The following table gives a brief description of each `RowState` enumeration value.</span></span>  
  
|<span data-ttu-id="a816b-108">Hodnota RowState</span><span class="sxs-lookup"><span data-stu-id="a816b-108">RowState value</span></span>|<span data-ttu-id="a816b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="a816b-109">Description</span></span>|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|<span data-ttu-id="a816b-110">Od posledního volání do `AcceptChanges` nebo od chvíle, kdy byl řádek vytvořen pomocí `DataAdapter.Fill`, nebyly provedeny žádné změny.</span><span class="sxs-lookup"><span data-stu-id="a816b-110">No changes have been made since the last call to `AcceptChanges` or since the row was created by `DataAdapter.Fill`.</span></span>|  
|<xref:System.Data.DataRowState.Added>|<span data-ttu-id="a816b-111">Řádek byl přidán do tabulky, ale `AcceptChanges` nebyl volán.</span><span class="sxs-lookup"><span data-stu-id="a816b-111">The row has been added to the table, but `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Modified>|<span data-ttu-id="a816b-112">Byl změněn nějaký element řádku.</span><span class="sxs-lookup"><span data-stu-id="a816b-112">Some element of the row has been changed.</span></span>|  
|<xref:System.Data.DataRowState.Deleted>|<span data-ttu-id="a816b-113">Řádek byl odstraněn z tabulky a `AcceptChanges` nebyl volán.</span><span class="sxs-lookup"><span data-stu-id="a816b-113">The row has been deleted from a table, and `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Detached>|<span data-ttu-id="a816b-114">Řádek není součástí žádného `DataRowCollection`řádku.</span><span class="sxs-lookup"><span data-stu-id="a816b-114">The row is not part of any `DataRowCollection`.</span></span> <span data-ttu-id="a816b-115">Nově vytvořený řádek je nastaven na `Detached`hodnotu. `RowState`</span><span class="sxs-lookup"><span data-stu-id="a816b-115">The `RowState` of a newly created row is set to `Detached`.</span></span> <span data-ttu-id="a816b-116">Po přidání nového `DataRow` do rozhraní `DataRowCollection` voláním `Add` metody je hodnota `RowState` vlastnosti nastavena na `Added`.</span><span class="sxs-lookup"><span data-stu-id="a816b-116">After the new `DataRow` is added to the `DataRowCollection` by calling the `Add` method, the value of the `RowState` property is set to `Added`.</span></span><br /><br /> <span data-ttu-id="a816b-117">`Detached`je také nastaveno pro řádek, `DataRowCollection` který byl odebrán z `Remove` `Delete` metody pomocí metody, nebo metodou následovanou `AcceptChanges` metodou.</span><span class="sxs-lookup"><span data-stu-id="a816b-117">`Detached` is also set for a row that has been removed from a `DataRowCollection` using the `Remove` method, or by the `Delete` method followed by the `AcceptChanges` method.</span></span>|  
  
 <span data-ttu-id="a816b-118">Když `AcceptChanges` je volána <xref:System.Data.DataSet>na, <xref:System.Data.DataTable> `Deleted` nebo <xref:System.Data.DataRow>, jsou odebrány všechny řádky se stavem řádku.</span><span class="sxs-lookup"><span data-stu-id="a816b-118">When `AcceptChanges` is called on a <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , or <xref:System.Data.DataRow>, all rows with a row state of `Deleted` are removed.</span></span> <span data-ttu-id="a816b-119">Zbývajícím řádkům je uveden stav `Unchanged`řádku a hodnoty `Original` ve verzi řádku `Current` jsou přepsány hodnotami verze řádku.</span><span class="sxs-lookup"><span data-stu-id="a816b-119">The remaining rows are given a row state of `Unchanged`, and the values in the `Original` row version are overwritten with the `Current` row version values.</span></span> <span data-ttu-id="a816b-120">Při `RejectChanges` volání se odeberou všechny řádky se `Added` stavem řádku.</span><span class="sxs-lookup"><span data-stu-id="a816b-120">When `RejectChanges` is called, all rows with a row state of `Added` are removed.</span></span> <span data-ttu-id="a816b-121">Zbývajícím řádkům je uveden stav `Unchanged`řádku a hodnoty `Current` ve verzi řádku `Original` jsou přepsány hodnotami verze řádku.</span><span class="sxs-lookup"><span data-stu-id="a816b-121">The remaining rows are given a row state of `Unchanged`, and the values in the `Current` row version are overwritten with the `Original` row version values.</span></span>  
  
 <span data-ttu-id="a816b-122">Můžete zobrazit různé verze řádku předáním <xref:System.Data.DataRowVersion> parametru s odkazem na sloupec, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a816b-122">You can view the different row versions of a row by passing a <xref:System.Data.DataRowVersion> parameter with the column reference, as shown in the following example.</span></span>  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 <span data-ttu-id="a816b-123">Následující tabulka obsahuje stručný popis každé `DataRowVersion` hodnoty výčtu.</span><span class="sxs-lookup"><span data-stu-id="a816b-123">The following table gives a brief description of each `DataRowVersion` enumeration value.</span></span>  
  
|<span data-ttu-id="a816b-124">Hodnota DataRowVersion</span><span class="sxs-lookup"><span data-stu-id="a816b-124">DataRowVersion value</span></span>|<span data-ttu-id="a816b-125">Popis</span><span class="sxs-lookup"><span data-stu-id="a816b-125">Description</span></span>|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|<span data-ttu-id="a816b-126">Aktuální hodnoty pro řádek</span><span class="sxs-lookup"><span data-stu-id="a816b-126">The current values for the row.</span></span> <span data-ttu-id="a816b-127">Tato verze řádku neexistuje pro řádky s `RowState`. `Deleted`</span><span class="sxs-lookup"><span data-stu-id="a816b-127">This row version does not exist for rows with a `RowState` of `Deleted`.</span></span>|  
|<xref:System.Data.DataRowVersion.Default>|<span data-ttu-id="a816b-128">Výchozí verze řádku pro určitý řádek</span><span class="sxs-lookup"><span data-stu-id="a816b-128">The default row version for a particular row.</span></span> <span data-ttu-id="a816b-129">Výchozí verze řádku `Added`pro, `Modified`nebo `Deleted` je `Current`.</span><span class="sxs-lookup"><span data-stu-id="a816b-129">The default row version for an `Added`, `Modified`, or `Deleted` row is `Current`.</span></span> <span data-ttu-id="a816b-130">Výchozí verze řádku pro `Detached` řádek je. `Proposed`</span><span class="sxs-lookup"><span data-stu-id="a816b-130">The default row version for a `Detached` row is `Proposed`.</span></span>|  
|<xref:System.Data.DataRowVersion.Original>|<span data-ttu-id="a816b-131">Původní hodnoty pro řádek</span><span class="sxs-lookup"><span data-stu-id="a816b-131">The original values for the row.</span></span> <span data-ttu-id="a816b-132">Tato verze řádku neexistuje pro řádky s `RowState`. `Added`</span><span class="sxs-lookup"><span data-stu-id="a816b-132">This row version does not exist for rows with a `RowState` of `Added`.</span></span>|  
|<xref:System.Data.DataRowVersion.Proposed>|<span data-ttu-id="a816b-133">Navrhované hodnoty pro řádek</span><span class="sxs-lookup"><span data-stu-id="a816b-133">The proposed values for the row.</span></span> <span data-ttu-id="a816b-134">Tato verze řádku existuje během operace Edit na řádku nebo pro řádek, který není součástí `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="a816b-134">This row version exists during an edit operation on a row, or for a row that is not part of a `DataRowCollection`.</span></span>|  
  
 <span data-ttu-id="a816b-135">Můžete otestovat, zda `DataRow` má konkrétní verzi řádku <xref:System.Data.DataRow.HasVersion%2A> voláním metody a předáním `DataRowVersion` jako argumentu.</span><span class="sxs-lookup"><span data-stu-id="a816b-135">You can test whether a `DataRow` has a particular row version by calling the <xref:System.Data.DataRow.HasVersion%2A> method and passing a `DataRowVersion` as an argument.</span></span> <span data-ttu-id="a816b-136">Například `DataRow.HasVersion(DataRowVersion.Original)` `AcceptChanges` vrátí `false` pro nově přidané řádky před voláním.</span><span class="sxs-lookup"><span data-stu-id="a816b-136">For example, `DataRow.HasVersion(DataRowVersion.Original)` will return `false` for newly added rows before `AcceptChanges` has been called.</span></span>  
  
 <span data-ttu-id="a816b-137">Následující příklad kódu zobrazuje hodnoty ze všech odstraněných řádků v tabulce.</span><span class="sxs-lookup"><span data-stu-id="a816b-137">The following code example displays the values in all the deleted rows of a table.</span></span> <span data-ttu-id="a816b-138">`Deleted`řádky nemají verzi `DataRowVersion.Original` řádku,takžejenutnépřipřístupukhodnotám`Current` sloupců předat.</span><span class="sxs-lookup"><span data-stu-id="a816b-138">`Deleted` rows do not have a `Current` row version, so you must pass `DataRowVersion.Original` when accessing the column values.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a816b-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a816b-139">See also</span></span>

- [<span data-ttu-id="a816b-140">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="a816b-140">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="a816b-141">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="a816b-141">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="a816b-142">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="a816b-142">DataAdapters and DataReaders</span></span>](../dataadapters-and-datareaders.md)
- [<span data-ttu-id="a816b-143">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a816b-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
