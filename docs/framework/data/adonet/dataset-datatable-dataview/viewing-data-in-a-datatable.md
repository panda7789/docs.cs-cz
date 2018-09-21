---
title: Zobrazení dat v datové tabulce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: de745633060dd4f7b1610492d0ff57ec7a4f545b
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46530216"
---
# <a name="viewing-data-in-a-datatable"></a><span data-ttu-id="19f94-102">Zobrazení dat v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="19f94-102">Viewing Data in a DataTable</span></span>
<span data-ttu-id="19f94-103">Můžete přístup k obsahu <xref:System.Data.DataTable> pomocí **řádky** a **sloupce** kolekce **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="19f94-103">You can access the contents of a <xref:System.Data.DataTable> by using the **Rows** and **Columns** collections of the **DataTable**.</span></span> <span data-ttu-id="19f94-104">Můžete také použít <xref:System.Data.DataTable.Select%2A> metoda vrátí podmnožiny dat v **DataTable** podle kritérií kritéria vyhledávání, řazení a řádek stavu.</span><span class="sxs-lookup"><span data-stu-id="19f94-104">You can also use the <xref:System.Data.DataTable.Select%2A> method to return subsets of the data in a **DataTable** according to criteria including search criteria, sort order, and row state.</span></span> <span data-ttu-id="19f94-105">Kromě toho můžete použít <xref:System.Data.DataRowCollection.Find%2A> metodu **kolekci DataRowCollection** při hledání konkrétního řádku pomocí hodnoty primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="19f94-105">Additionally, you can use the <xref:System.Data.DataRowCollection.Find%2A> method of the **DataRowCollection** when searching for a particular row using a primary key value.</span></span>  
  
 <span data-ttu-id="19f94-106">**Vyberte** metodu **DataTable** objekt vrací sadu <xref:System.Data.DataRow> objekty, které odpovídají zadaným kritériím.</span><span class="sxs-lookup"><span data-stu-id="19f94-106">The **Select** method of the **DataTable** object returns a set of <xref:System.Data.DataRow> objects that match the specified criteria.</span></span> <span data-ttu-id="19f94-107">**Vyberte** přebírá nepovinné argumenty výrazu filtru, řadicí výraz, a **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="19f94-107">**Select** takes optional arguments of a filter expression, sort expression, and **DataViewRowState**.</span></span> <span data-ttu-id="19f94-108">Výraz filtru identifikuje řádky, které chcete vrátit na základě **DataColumn** hodnoty, jako například `LastName = 'Smith'`.</span><span class="sxs-lookup"><span data-stu-id="19f94-108">The filter expression identifies which rows to return based on **DataColumn** values, such as `LastName = 'Smith'`.</span></span> <span data-ttu-id="19f94-109">Výraz řazení dodržuje standardní konvence SQL pro řazení sloupců, třeba `LastName ASC, FirstName ASC`.</span><span class="sxs-lookup"><span data-stu-id="19f94-109">The sort expression follows standard SQL conventions for ordering columns, for example `LastName ASC, FirstName ASC`.</span></span> <span data-ttu-id="19f94-110">Pravidla týkající se vytváření výrazů, najdete v článku <xref:System.Data.DataColumn.Expression%2A> vlastnost **DataColumn** třídy.</span><span class="sxs-lookup"><span data-stu-id="19f94-110">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="19f94-111">Pokud provádíte počet volání **vyberte** metodu **DataTable**, může zvýšit výkon tím, že vytvoříte první <xref:System.Data.DataView> pro **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="19f94-111">If you are performing a number of calls to the **Select** method of a **DataTable**, you can increase performance by first creating a <xref:System.Data.DataView> for the **DataTable**.</span></span> <span data-ttu-id="19f94-112">Vytváří **DataView** indexuje řádky tabulky.</span><span class="sxs-lookup"><span data-stu-id="19f94-112">Creating the **DataView** indexes the rows of the table.</span></span> <span data-ttu-id="19f94-113">**Vyberte** metoda pak usees, které indexu, což výrazně zkrátí čas k vygenerování výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="19f94-113">The **Select** method then usees that index, significantly reducing the time to generate the query result.</span></span> <span data-ttu-id="19f94-114">Informace o vytváření **DataView** pro **DataTable**, naleznete v tématu [zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).</span><span class="sxs-lookup"><span data-stu-id="19f94-114">For information about creating a **DataView** for a **DataTable**, see [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).</span></span>  
  
 <span data-ttu-id="19f94-115">**Vyberte** metoda určí na základě verze řádků, které chcete zobrazit nebo pracovat <xref:System.Data.DataViewRowState>.</span><span class="sxs-lookup"><span data-stu-id="19f94-115">The **Select** method determines which version of the rows to view or manipulate based on a <xref:System.Data.DataViewRowState>.</span></span> <span data-ttu-id="19f94-116">Následující tabulka popisuje možné **DataViewRowState** hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="19f94-116">The following table describes the possible **DataViewRowState** enumeration values.</span></span>  
  
|<span data-ttu-id="19f94-117">Hodnota DataViewRowState</span><span class="sxs-lookup"><span data-stu-id="19f94-117">DataViewRowState value</span></span>|<span data-ttu-id="19f94-118">Popis</span><span class="sxs-lookup"><span data-stu-id="19f94-118">Description</span></span>|  
|----------------------------|-----------------|  
|<span data-ttu-id="19f94-119">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="19f94-119">**CurrentRows**</span></span>|<span data-ttu-id="19f94-120">Aktuální řádky včetně beze změny, přidání a upravené řádky.</span><span class="sxs-lookup"><span data-stu-id="19f94-120">Current rows including unchanged, added, and modified rows.</span></span>|  
|<span data-ttu-id="19f94-121">**Odstranit**</span><span class="sxs-lookup"><span data-stu-id="19f94-121">**Deleted**</span></span>|<span data-ttu-id="19f94-122">Odstraněný řádek.</span><span class="sxs-lookup"><span data-stu-id="19f94-122">A deleted row.</span></span>|  
|<span data-ttu-id="19f94-123">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="19f94-123">**ModifiedCurrent**</span></span>|<span data-ttu-id="19f94-124">Aktuální verzi, která je upravená verze původní data.</span><span class="sxs-lookup"><span data-stu-id="19f94-124">A current version, which is a modified version of original data.</span></span> <span data-ttu-id="19f94-125">(Viz **ModifiedOriginal**.)</span><span class="sxs-lookup"><span data-stu-id="19f94-125">(See **ModifiedOriginal**.)</span></span>|  
|<span data-ttu-id="19f94-126">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="19f94-126">**ModifiedOriginal**</span></span>|<span data-ttu-id="19f94-127">Původní verzi všechny změněné řádky.</span><span class="sxs-lookup"><span data-stu-id="19f94-127">The original version of all modified rows.</span></span> <span data-ttu-id="19f94-128">Aktuální verze je k dispozici pomocí **ModifiedCurrent**.</span><span class="sxs-lookup"><span data-stu-id="19f94-128">The current version is available using **ModifiedCurrent**.</span></span>|  
|<span data-ttu-id="19f94-129">**Přidat**</span><span class="sxs-lookup"><span data-stu-id="19f94-129">**Added**</span></span>|<span data-ttu-id="19f94-130">Nový řádek.</span><span class="sxs-lookup"><span data-stu-id="19f94-130">A new row.</span></span>|  
|<span data-ttu-id="19f94-131">**None**</span><span class="sxs-lookup"><span data-stu-id="19f94-131">**None**</span></span>|<span data-ttu-id="19f94-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="19f94-132">None.</span></span>|  
|<span data-ttu-id="19f94-133">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="19f94-133">**OriginalRows**</span></span>|<span data-ttu-id="19f94-134">Původní řádky, včetně beze změny a odstranit řádky.</span><span class="sxs-lookup"><span data-stu-id="19f94-134">Original rows, including unchanged and deleted rows.</span></span>|  
|<span data-ttu-id="19f94-135">**beze změny**</span><span class="sxs-lookup"><span data-stu-id="19f94-135">**Unchanged**</span></span>|<span data-ttu-id="19f94-136">Beze změny řádků.</span><span class="sxs-lookup"><span data-stu-id="19f94-136">An unchanged row.</span></span>|  
  
 <span data-ttu-id="19f94-137">V následujícím příkladu **datovou sadu** objektu je filtrována tak, aby pouze pracujete s řádky jehož **DataViewRowState** je nastavena na **CurrentRows**.</span><span class="sxs-lookup"><span data-stu-id="19f94-137">In the following example, the **DataSet** object is filtered so that you are only working with rows whose **DataViewRowState** is set to **CurrentRows**.</span></span>  
  
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
  
 <span data-ttu-id="19f94-138">**Vyberte** metodu je možné vrátit řádky s různými **RowState** hodnoty nebo hodnot polí.</span><span class="sxs-lookup"><span data-stu-id="19f94-138">The **Select** method can be used to return rows with differing **RowState** values or field values.</span></span> <span data-ttu-id="19f94-139">Následující příklad vrátí **DataRow** pole, které odkazuje na všechny řádky, které se odstranily a vrátí jiný **DataRow** pole, které odkazuje na všechny řádky, seřazené podle **CustLName**, kde **CustID** sloupec je větší než 5.</span><span class="sxs-lookup"><span data-stu-id="19f94-139">The following example returns a **DataRow** array that references all rows that have been deleted, and returns another **DataRow** array that references all rows, ordered by **CustLName**, where the **CustID** column is greater than 5.</span></span> <span data-ttu-id="19f94-140">Informace o tom, jak zobrazit informace v **odstraněné** řádek, přečtěte si téma [stavy řádků a verze řádků](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="19f94-140">For information about how to view the information in the **Deleted** row, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="19f94-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="19f94-141">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataViewRowState>  
 [<span data-ttu-id="19f94-142">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="19f94-142">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="19f94-143">Stavy řádků a verze řádků</span><span class="sxs-lookup"><span data-stu-id="19f94-143">Row States and Row Versions</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [<span data-ttu-id="19f94-144">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="19f94-144">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
