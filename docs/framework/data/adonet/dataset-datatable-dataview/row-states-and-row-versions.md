---
title: Stavy řádků a verze řádků
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 629e8b0bea1cd5c1dd80409acd7c03e0e033b5bc
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43880571"
---
# <a name="row-states-and-row-versions"></a><span data-ttu-id="77582-102">Stavy řádků a verze řádků</span><span class="sxs-lookup"><span data-stu-id="77582-102">Row States and Row Versions</span></span>
<span data-ttu-id="77582-103">ADO.NET spravuje řádků v tabulkách stavy řádků a verze.</span><span class="sxs-lookup"><span data-stu-id="77582-103">ADO.NET manages rows in tables using row states and versions.</span></span> <span data-ttu-id="77582-104">Stav řádek znamená stavový řádek; verze řádků Udržovat hodnoty uložené v řádku, jako jsou změny, včetně aktuální a původní, výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="77582-104">A row state indicates the status of a row; row versions maintain the values stored in a row as it is modified, including current, original, and default values.</span></span> <span data-ttu-id="77582-105">Například po provedení změny na sloupec v řádku, řádku budou mít stav řádku `Modified`, a dvě verze řádků: `Current`, který obsahuje hodnoty aktuálního řádku a `Original`, obsahující hodnoty řádků dříve, než byl sloupec upravit.</span><span class="sxs-lookup"><span data-stu-id="77582-105">For example, after you have made a modification to a column in a row, the row will have a row state of `Modified`, and two row versions: `Current`, which contains the current row values, and `Original`, which contains the row values before the column was modified.</span></span>  
  
 <span data-ttu-id="77582-106">Každý <xref:System.Data.DataRow> má objekt <xref:System.Data.DataRow.RowState%2A> vlastnost, která můžete zkoumat, chcete-li zjistit aktuální stav řádku.</span><span class="sxs-lookup"><span data-stu-id="77582-106">Each <xref:System.Data.DataRow> object has a <xref:System.Data.DataRow.RowState%2A> property that you can examine to determine the current state of the row.</span></span> <span data-ttu-id="77582-107">Následující tabulka obsahuje stručný popis jednotlivých `RowState` hodnota výčtu.</span><span class="sxs-lookup"><span data-stu-id="77582-107">The following table gives a brief description of each `RowState` enumeration value.</span></span>  
  
|<span data-ttu-id="77582-108">Hodnota RowState</span><span class="sxs-lookup"><span data-stu-id="77582-108">RowState value</span></span>|<span data-ttu-id="77582-109">Popis</span><span class="sxs-lookup"><span data-stu-id="77582-109">Description</span></span>|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|<span data-ttu-id="77582-110">Byly provedeny žádné změny od posledního volání `AcceptChanges` nebo od řádku vytvořil `DataAdapter.Fill`.</span><span class="sxs-lookup"><span data-stu-id="77582-110">No changes have been made since the last call to `AcceptChanges` or since the row was created by `DataAdapter.Fill`.</span></span>|  
|<xref:System.Data.DataRowState.Added>|<span data-ttu-id="77582-111">Řádek byl přidán do tabulky, ale `AcceptChanges` se nevolala.</span><span class="sxs-lookup"><span data-stu-id="77582-111">The row has been added to the table, but `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Modified>|<span data-ttu-id="77582-112">Některé prvek řádku byl změněn.</span><span class="sxs-lookup"><span data-stu-id="77582-112">Some element of the row has been changed.</span></span>|  
|<xref:System.Data.DataRowState.Deleted>|<span data-ttu-id="77582-113">Na řádku byla odstraněna z tabulky, a `AcceptChanges` se nevolala.</span><span class="sxs-lookup"><span data-stu-id="77582-113">The row has been deleted from a table, and `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Detached>|<span data-ttu-id="77582-114">Řádek není součástí žádné `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="77582-114">The row is not part of any `DataRowCollection`.</span></span> <span data-ttu-id="77582-115">`RowState` Nově vytvořený řádku je nastavena na `Detached`.</span><span class="sxs-lookup"><span data-stu-id="77582-115">The `RowState` of a newly created row is set to `Detached`.</span></span> <span data-ttu-id="77582-116">Po nové `DataRow` se přidá do `DataRowCollection` voláním `Add` metoda, hodnota `RowState` je nastavena na `Added`.</span><span class="sxs-lookup"><span data-stu-id="77582-116">After the new `DataRow` is added to the `DataRowCollection` by calling the `Add` method, the value of the `RowState` property is set to `Added`.</span></span><br /><br /> <span data-ttu-id="77582-117">`Detached` je také nastavena pro řádek, který byl odebrán z `DataRowCollection` pomocí `Remove` metodu, nebo `Delete` následuje metoda `AcceptChanges` – metoda.</span><span class="sxs-lookup"><span data-stu-id="77582-117">`Detached` is also set for a row that has been removed from a `DataRowCollection` using the `Remove` method, or by the `Delete` method followed by the `AcceptChanges` method.</span></span>|  
  
 <span data-ttu-id="77582-118">Když `AcceptChanges` je volán na <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , nebo <xref:System.Data.DataRow>, všechny řádky se stavem řádek `Deleted` se odeberou.</span><span class="sxs-lookup"><span data-stu-id="77582-118">When `AcceptChanges` is called on a <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , or <xref:System.Data.DataRow>, all rows with a row state of `Deleted` are removed.</span></span> <span data-ttu-id="77582-119">Zbývající řádky jsou uvedeny ve stavu řádku `Unchanged`a hodnotami ve `Original` jsou přepsány verze řádku `Current` řádek hodnoty verze.</span><span class="sxs-lookup"><span data-stu-id="77582-119">The remaining rows are given a row state of `Unchanged`, and the values in the `Original` row version are overwritten with the `Current` row version values.</span></span> <span data-ttu-id="77582-120">Když `RejectChanges` nazývá všechny řádky se stavem řádek `Added` se odeberou.</span><span class="sxs-lookup"><span data-stu-id="77582-120">When `RejectChanges` is called, all rows with a row state of `Added` are removed.</span></span> <span data-ttu-id="77582-121">Zbývající řádky jsou uvedeny ve stavu řádku `Unchanged`a hodnotami ve `Current` jsou přepsány verze řádku `Original` řádek hodnoty verze.</span><span class="sxs-lookup"><span data-stu-id="77582-121">The remaining rows are given a row state of `Unchanged`, and the values in the `Current` row version are overwritten with the `Original` row version values.</span></span>  
  
 <span data-ttu-id="77582-122">Verze odlišný řádek řádku můžete zobrazit pomocí předání <xref:System.Data.DataRowVersion> parametr odkazem na sloupec, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="77582-122">You can view the different row versions of a row by passing a <xref:System.Data.DataRowVersion> parameter with the column reference, as shown in the following example.</span></span>  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 <span data-ttu-id="77582-123">Následující tabulka obsahuje stručný popis jednotlivých `DataRowVersion` hodnota výčtu.</span><span class="sxs-lookup"><span data-stu-id="77582-123">The following table gives a brief description of each `DataRowVersion` enumeration value.</span></span>  
  
|<span data-ttu-id="77582-124">Hodnota DataRowVersion</span><span class="sxs-lookup"><span data-stu-id="77582-124">DataRowVersion value</span></span>|<span data-ttu-id="77582-125">Popis</span><span class="sxs-lookup"><span data-stu-id="77582-125">Description</span></span>|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|<span data-ttu-id="77582-126">Aktuální hodnoty řádku.</span><span class="sxs-lookup"><span data-stu-id="77582-126">The current values for the row.</span></span> <span data-ttu-id="77582-127">Tato verze řádků pro řádky s neexistuje `RowState` z `Deleted`.</span><span class="sxs-lookup"><span data-stu-id="77582-127">This row version does not exist for rows with a `RowState` of `Deleted`.</span></span>|  
|<xref:System.Data.DataRowVersion.Default>|<span data-ttu-id="77582-128">Výchozí verze řádků pro konkrétní řádek.</span><span class="sxs-lookup"><span data-stu-id="77582-128">The default row version for a particular row.</span></span> <span data-ttu-id="77582-129">Výchozí verze řádků pro `Added`, `Modified`, nebo `Deleted` řádek je `Current`.</span><span class="sxs-lookup"><span data-stu-id="77582-129">The default row version for an `Added`, `Modified`, or `Deleted` row is `Current`.</span></span> <span data-ttu-id="77582-130">Výchozí verze řádků pro `Detached` řádek je `Proposed`.</span><span class="sxs-lookup"><span data-stu-id="77582-130">The default row version for a `Detached` row is `Proposed`.</span></span>|  
|<xref:System.Data.DataRowVersion.Original>|<span data-ttu-id="77582-131">Původní hodnoty řádku.</span><span class="sxs-lookup"><span data-stu-id="77582-131">The original values for the row.</span></span> <span data-ttu-id="77582-132">Tato verze řádků pro řádky s neexistuje `RowState` z `Added`.</span><span class="sxs-lookup"><span data-stu-id="77582-132">This row version does not exist for rows with a `RowState` of `Added`.</span></span>|  
|<xref:System.Data.DataRowVersion.Proposed>|<span data-ttu-id="77582-133">Navrhované hodnoty řádku.</span><span class="sxs-lookup"><span data-stu-id="77582-133">The proposed values for the row.</span></span> <span data-ttu-id="77582-134">Tato verze řádku existuje během operace úpravy na řádku, nebo pro řádek, který není součástí `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="77582-134">This row version exists during an edit operation on a row, or for a row that is not part of a `DataRowCollection`.</span></span>|  
  
 <span data-ttu-id="77582-135">Můžete otestovat, jestli `DataRow` má verzi konkrétního řádku voláním <xref:System.Data.DataRow.HasVersion%2A> metoda a předávání `DataRowVersion` jako argument.</span><span class="sxs-lookup"><span data-stu-id="77582-135">You can test whether a `DataRow` has a particular row version by calling the <xref:System.Data.DataRow.HasVersion%2A> method and passing a `DataRowVersion` as an argument.</span></span> <span data-ttu-id="77582-136">Například `DataRow.HasVersion(DataRowVersion.Original)` vrátí `false` pro nově přidané řádky před `AcceptChanges` byla volána.</span><span class="sxs-lookup"><span data-stu-id="77582-136">For example, `DataRow.HasVersion(DataRowVersion.Original)` will return `false` for newly added rows before `AcceptChanges` has been called.</span></span>  
  
 <span data-ttu-id="77582-137">Následující příklad kódu zobrazuje hodnoty v odstraněné řádky tabulky.</span><span class="sxs-lookup"><span data-stu-id="77582-137">The following code example displays the values in all the deleted rows of a table.</span></span> <span data-ttu-id="77582-138">`Deleted` není nutné řádků `Current` verze řádku, takže je nutné předat `DataRowVersion.Original` při přístupu k hodnot sloupců.</span><span class="sxs-lookup"><span data-stu-id="77582-138">`Deleted` rows do not have a `Current` row version, so you must pass `DataRowVersion.Original` when accessing the column values.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="77582-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="77582-139">See Also</span></span>  
 [<span data-ttu-id="77582-140">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="77582-140">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="77582-141">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="77582-141">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="77582-142">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="77582-142">DataAdapters and DataReaders</span></span>](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="77582-143">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="77582-143">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
