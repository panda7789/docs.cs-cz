---
title: Kopírování obsahu datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: bee91a6406fd48894580ce6223a5682dbadab380
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757291"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="92cdc-102">Kopírování obsahu datové sady</span><span class="sxs-lookup"><span data-stu-id="92cdc-102">Copying DataSet Contents</span></span>
<span data-ttu-id="92cdc-103">Můžete vytvořit kopii <xref:System.Data.DataSet> , mohli pracovat s daty, aniž by to ovlivnilo původní data nebo pracovat s podmnožinu dat z **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="92cdc-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="92cdc-104">Při kopírování **datovou sadu**, můžete:</span><span class="sxs-lookup"><span data-stu-id="92cdc-104">When copying a **DataSet**, you can:</span></span>  
  
-   <span data-ttu-id="92cdc-105">Vytvořit přesnou kopii **datovou sadu**, včetně schéma, data, informace o stavu řádku a verze řádku.</span><span class="sxs-lookup"><span data-stu-id="92cdc-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
-   <span data-ttu-id="92cdc-106">Vytvoření **datovou sadu** obsahující schéma z existující **datovou sadu**, ale pouze řádky, které byly upraveny.</span><span class="sxs-lookup"><span data-stu-id="92cdc-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="92cdc-107">Vrátí všechny řádky, které byly upraveny, nebo zadat konkrétní **DataRowState**.</span><span class="sxs-lookup"><span data-stu-id="92cdc-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="92cdc-108">Další informace o stavy řádků najdete v tématu [stavy řádků a verze řádku](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="92cdc-108">For more information about row states, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
-   <span data-ttu-id="92cdc-109">Zkopírujte schéma nebo relační struktura z **datovou sadu** pouze bez kopírování žádné řádky.</span><span class="sxs-lookup"><span data-stu-id="92cdc-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="92cdc-110">Řádky se dají importovat do existující <xref:System.Data.DataTable> pomocí <xref:System.Data.DataTable.ImportRow%2A>.</span><span class="sxs-lookup"><span data-stu-id="92cdc-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="92cdc-111">Chcete-li vytvořit přesný kopii **datovou sadu** zahrnující schéma a data, použijte <xref:System.Data.DataSet.Copy%2A> metodu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="92cdc-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="92cdc-112">Následující příklad kódu ukazuje, jak vytvořit přesnou kopii **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="92cdc-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="92cdc-113">Vytvořit kopii **datovou sadu** schéma a pouze na data představující, který obsahuje **Added**, **změněné**, nebo **odstraněné** řádky, použijte <xref:System.Data.DataSet.GetChanges%2A> metodu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="92cdc-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="92cdc-114">Můžete také použít **GetChanges –** vrátit pouze sloupce se stavem zadaný řádek předáním **DataRowState** hodnota při volání metody **GetChanges –**.</span><span class="sxs-lookup"><span data-stu-id="92cdc-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="92cdc-115">Následující příklad kódu ukazuje, jak předat **DataRowState** při volání metody **GetChanges –**.</span><span class="sxs-lookup"><span data-stu-id="92cdc-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 <span data-ttu-id="92cdc-116">Vytvořit kopii **datovou sadu** zahrnující schéma, použijte <xref:System.Data.DataSet.Clone%2A> metodu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="92cdc-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="92cdc-117">Můžete také přidat existující řádky do klonované **datovou sadu** pomocí **ImportRow** metodu **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="92cdc-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="92cdc-118">**ImportRow** přidá data, stav řádku a informace o verzi řádek zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="92cdc-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="92cdc-119">Hodnoty ve sloupcích se přidají jenom kde odpovídá názvu sloupce a data typ je kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="92cdc-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="92cdc-120">Následující příklad kódu vytvoří klon **datovou sadu** a potom přidá řádky z původní **datovou sadu** k **zákazníci** tabulky v **datové sady**  klon pro zákazníky, kde **země** sloupec obsahuje hodnotu "Německo".</span><span class="sxs-lookup"><span data-stu-id="92cdc-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =   
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a><span data-ttu-id="92cdc-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="92cdc-121">See Also</span></span>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="92cdc-122">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="92cdc-122">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="92cdc-123">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="92cdc-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
