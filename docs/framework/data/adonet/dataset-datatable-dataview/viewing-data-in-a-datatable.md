---
title: Zobrazení dat v datové tabulce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: ea92b8a5e46bdaa8e94756cd28a3fbcb2789d7b3
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204386"
---
# <a name="viewing-data-in-a-datatable"></a><span data-ttu-id="79aec-102">Zobrazení dat v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="79aec-102">Viewing Data in a DataTable</span></span>

<span data-ttu-id="79aec-103">K <xref:System.Data.DataTable> obsahu můžete přistupovat pomocí kolekcí **řádky** a **sloupce** **objektu DataTable**.</span><span class="sxs-lookup"><span data-stu-id="79aec-103">You can access the contents of a <xref:System.Data.DataTable> by using the **Rows** and **Columns** collections of the **DataTable**.</span></span> <span data-ttu-id="79aec-104">Můžete také použít <xref:System.Data.DataTable.Select%2A> metodu pro vrácení podmnožiny dat v **objektu DataTable** podle kritérií, včetně kritérií hledání, pořadí řazení a stavu řádku.</span><span class="sxs-lookup"><span data-stu-id="79aec-104">You can also use the <xref:System.Data.DataTable.Select%2A> method to return subsets of the data in a **DataTable** according to criteria including search criteria, sort order, and row state.</span></span> <span data-ttu-id="79aec-105">Kromě toho můžete použít <xref:System.Data.DataRowCollection.Find%2A> metodu **kolekci DataRowCollection** při hledání konkrétního řádku pomocí hodnoty primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="79aec-105">Additionally, you can use the <xref:System.Data.DataRowCollection.Find%2A> method of the **DataRowCollection** when searching for a particular row using a primary key value.</span></span>

<span data-ttu-id="79aec-106">Metoda **Select** objektu **DataTable** vrací sadu <xref:System.Data.DataRow> objektů, které odpovídají zadaným kritériím.</span><span class="sxs-lookup"><span data-stu-id="79aec-106">The **Select** method of the **DataTable** object returns a set of <xref:System.Data.DataRow> objects that match the specified criteria.</span></span> <span data-ttu-id="79aec-107">**Vyberte možnost** přebírá volitelné argumenty výrazu filtru, výraz řazení a **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="79aec-107">**Select** takes optional arguments of a filter expression, sort expression, and **DataViewRowState**.</span></span> <span data-ttu-id="79aec-108">Výraz filtru určuje, které řádky se mají vrátit na základě hodnot DataColumn, například `LastName = 'Smith'`.</span><span class="sxs-lookup"><span data-stu-id="79aec-108">The filter expression identifies which rows to return based on **DataColumn** values, such as `LastName = 'Smith'`.</span></span> <span data-ttu-id="79aec-109">Výraz řazení se řídí standardními konvencemi SQL pro řazení sloupců, `LastName ASC, FirstName ASC`například.</span><span class="sxs-lookup"><span data-stu-id="79aec-109">The sort expression follows standard SQL conventions for ordering columns, for example `LastName ASC, FirstName ASC`.</span></span> <span data-ttu-id="79aec-110">Pravidla týkající se psaní výrazů naleznete v tématu <xref:System.Data.DataColumn.Expression%2A> vlastnost třídy DataColumn.</span><span class="sxs-lookup"><span data-stu-id="79aec-110">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>

> [!TIP]
> <span data-ttu-id="79aec-111">Provádíte-li několik volání metody **Select** **objektu DataTable**, lze zvýšit výkon tím, že <xref:System.Data.DataView> nejprve vytvoříte objekt pro **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="79aec-111">If you are performing a number of calls to the **Select** method of a **DataTable**, you can increase performance by first creating a <xref:System.Data.DataView> for the **DataTable**.</span></span> <span data-ttu-id="79aec-112">Vytvořením objektu **DataView** se naindexuje řádky tabulky.</span><span class="sxs-lookup"><span data-stu-id="79aec-112">Creating the **DataView** indexes the rows of the table.</span></span> <span data-ttu-id="79aec-113">Metoda **Select** pak použije tento index, což významně zkracuje čas k vygenerování výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="79aec-113">The **Select** method then uses that index, significantly reducing the time to generate the query result.</span></span> <span data-ttu-id="79aec-114">Informace o vytvoření objektu **DataView** pro **objekt DataTable**naleznete v tématu [](dataviews.md)DataViews.</span><span class="sxs-lookup"><span data-stu-id="79aec-114">For information about creating a **DataView** for a **DataTable**, see [DataViews](dataviews.md).</span></span>

<span data-ttu-id="79aec-115">Metoda **Select** určuje, která verze řádků se má zobrazit nebo manipulovat na základě <xref:System.Data.DataViewRowState>.</span><span class="sxs-lookup"><span data-stu-id="79aec-115">The **Select** method determines which version of the rows to view or manipulate based on a <xref:System.Data.DataViewRowState>.</span></span> <span data-ttu-id="79aec-116">Následující tabulka popisuje možné hodnoty výčtu **DataViewRowState** .</span><span class="sxs-lookup"><span data-stu-id="79aec-116">The following table describes the possible **DataViewRowState** enumeration values.</span></span>

|<span data-ttu-id="79aec-117">Hodnota DataViewRowState</span><span class="sxs-lookup"><span data-stu-id="79aec-117">DataViewRowState value</span></span>|<span data-ttu-id="79aec-118">Popis</span><span class="sxs-lookup"><span data-stu-id="79aec-118">Description</span></span>|
|----------------------------|-----------------|
|<span data-ttu-id="79aec-119">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="79aec-119">**CurrentRows**</span></span>|<span data-ttu-id="79aec-120">Aktuální řádky, včetně nezměněných, přidaných a upravených řádků.</span><span class="sxs-lookup"><span data-stu-id="79aec-120">Current rows including unchanged, added, and modified rows.</span></span>|
|<span data-ttu-id="79aec-121">**Odstraňování**</span><span class="sxs-lookup"><span data-stu-id="79aec-121">**Deleted**</span></span>|<span data-ttu-id="79aec-122">Odstraněný řádek.</span><span class="sxs-lookup"><span data-stu-id="79aec-122">A deleted row.</span></span>|
|<span data-ttu-id="79aec-123">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="79aec-123">**ModifiedCurrent**</span></span>|<span data-ttu-id="79aec-124">Aktuální verze, která je upravená verze původních dat.</span><span class="sxs-lookup"><span data-stu-id="79aec-124">A current version, which is a modified version of original data.</span></span> <span data-ttu-id="79aec-125">(Viz **ModifiedOriginal**.)</span><span class="sxs-lookup"><span data-stu-id="79aec-125">(See **ModifiedOriginal**.)</span></span>|
|<span data-ttu-id="79aec-126">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="79aec-126">**ModifiedOriginal**</span></span>|<span data-ttu-id="79aec-127">Původní verze všech upravených řádků.</span><span class="sxs-lookup"><span data-stu-id="79aec-127">The original version of all modified rows.</span></span> <span data-ttu-id="79aec-128">Aktuální verze je k dispozici pomocí **ModifiedCurrent**.</span><span class="sxs-lookup"><span data-stu-id="79aec-128">The current version is available using **ModifiedCurrent**.</span></span>|
|<span data-ttu-id="79aec-129">**Přidat**</span><span class="sxs-lookup"><span data-stu-id="79aec-129">**Added**</span></span>|<span data-ttu-id="79aec-130">Nový řádek.</span><span class="sxs-lookup"><span data-stu-id="79aec-130">A new row.</span></span>|
|<span data-ttu-id="79aec-131">**Žádné**</span><span class="sxs-lookup"><span data-stu-id="79aec-131">**None**</span></span>|<span data-ttu-id="79aec-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="79aec-132">None.</span></span>|
|<span data-ttu-id="79aec-133">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="79aec-133">**OriginalRows**</span></span>|<span data-ttu-id="79aec-134">Původní řádky, včetně nezměněných a odstraněných řádků.</span><span class="sxs-lookup"><span data-stu-id="79aec-134">Original rows, including unchanged and deleted rows.</span></span>|
|<span data-ttu-id="79aec-135">**Oproti**</span><span class="sxs-lookup"><span data-stu-id="79aec-135">**Unchanged**</span></span>|<span data-ttu-id="79aec-136">Nezměněný řádek.</span><span class="sxs-lookup"><span data-stu-id="79aec-136">An unchanged row.</span></span>|

<span data-ttu-id="79aec-137">V následujícím příkladu je objekt **DataSet** filtrován, takže pracujete pouze s řádky, jejichž **DataViewRowState** je nastaven na **CurrentRows**.</span><span class="sxs-lookup"><span data-stu-id="79aec-137">In the following example, the **DataSet** object is filtered so that you are only working with rows whose **DataViewRowState** is set to **CurrentRows**.</span></span>

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

<span data-ttu-id="79aec-138">Metodu **Select** lze použít k vrácení řádků s různými hodnotami **RowState** nebo hodnotami polí.</span><span class="sxs-lookup"><span data-stu-id="79aec-138">The **Select** method can be used to return rows with differing **RowState** values or field values.</span></span> <span data-ttu-id="79aec-139">Následující příklad vrátí pole **DataRow** , které odkazuje na všechny řádky, které byly odstraněny, a vrátí další pole **DataRow** , které odkazuje na všechny řádky seřazené podle **CustLName**, kde sloupec **custid** je větší než 5.</span><span class="sxs-lookup"><span data-stu-id="79aec-139">The following example returns a **DataRow** array that references all rows that have been deleted, and returns another **DataRow** array that references all rows, ordered by **CustLName**, where the **CustID** column is greater than 5.</span></span> <span data-ttu-id="79aec-140">Informace o tom, jak zobrazit informace na odstraněném řádku, najdete v tématu [stavy řádků a verze řádků](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="79aec-140">For information about how to view the information in the **Deleted** row, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="79aec-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79aec-141">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataViewRowState>
- [<span data-ttu-id="79aec-142">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="79aec-142">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="79aec-143">Stavy řádků a verze řádků</span><span class="sxs-lookup"><span data-stu-id="79aec-143">Row States and Row Versions</span></span>](row-states-and-row-versions.md)
- [<span data-ttu-id="79aec-144">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="79aec-144">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
