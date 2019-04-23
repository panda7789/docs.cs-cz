---
title: Kopírování obsahu datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: cb2a172ac4e6a0ce4852f4c7cf7044583d9ab6c4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077757"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="a010f-102">Kopírování obsahu datové sady</span><span class="sxs-lookup"><span data-stu-id="a010f-102">Copying DataSet Contents</span></span>
<span data-ttu-id="a010f-103">Můžete vytvořit kopii <xref:System.Data.DataSet> tak, aby můžete pracovat s daty, aniž by to ovlivnilo původní data ani pracovní obsahující jenom určitou podmnožinu dat z **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="a010f-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="a010f-104">Při kopírování **datovou sadu**, můžete:</span><span class="sxs-lookup"><span data-stu-id="a010f-104">When copying a **DataSet**, you can:</span></span>  
  
-   <span data-ttu-id="a010f-105">Vytvoření přesnou kopii **datovou sadu**, včetně schéma, data, informace o stavu řádků a verze řádků.</span><span class="sxs-lookup"><span data-stu-id="a010f-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
-   <span data-ttu-id="a010f-106">Vytvoření **datovou sadu** , která obsahuje schéma z existujícího **datovou sadu**, ale pouze řádky, které byly změněny.</span><span class="sxs-lookup"><span data-stu-id="a010f-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="a010f-107">Vrátí všechny řádky, které byly změněny, nebo zadat konkrétní **hodnotou DataRowState**.</span><span class="sxs-lookup"><span data-stu-id="a010f-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="a010f-108">Další informace o stavy řádků, naleznete v tématu [stavy řádků a verze řádků](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="a010f-108">For more information about row states, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
-   <span data-ttu-id="a010f-109">Kopie schématu nebo relační struktury **datovou sadu** pouze, bez kopírování žádné řádky.</span><span class="sxs-lookup"><span data-stu-id="a010f-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="a010f-110">Řádky se dají importovat do existující <xref:System.Data.DataTable> pomocí <xref:System.Data.DataTable.ImportRow%2A>.</span><span class="sxs-lookup"><span data-stu-id="a010f-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="a010f-111">K vytvoření přesnou kopii **datovou sadu** , který obsahuje schéma a data, použijte <xref:System.Data.DataSet.Copy%2A> metodu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="a010f-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="a010f-112">Následující příklad kódu ukazuje, jak vytvořit přesnou kopii **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="a010f-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="a010f-113">Chcete-li vytvořit kopii **datovou sadu** , který obsahuje schéma a pouze na data představující **přidané**, **změněné**, nebo **odstraněné** řádků, použijte <xref:System.Data.DataSet.GetChanges%2A> metodu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="a010f-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="a010f-114">Můžete také použít **GetChanges –** vrátit pouze řádky se stavem zadaný řádek tím, že předáte **hodnotou DataRowState** hodnotu při volání metody **GetChanges –**.</span><span class="sxs-lookup"><span data-stu-id="a010f-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="a010f-115">Následující příklad kódu ukazuje, jak předat **hodnotou DataRowState** při volání metody **GetChanges –**.</span><span class="sxs-lookup"><span data-stu-id="a010f-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
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
  
 <span data-ttu-id="a010f-116">Chcete-li vytvořit kopii **datovou sadu** , který obsahuje pouze schéma, použijte <xref:System.Data.DataSet.Clone%2A> metodu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="a010f-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="a010f-117">Můžete také přidat existující řádky do klonované **datovou sadu** pomocí **ImportRow** metodu **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="a010f-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="a010f-118">**ImportRow** přidá do zadané tabulky dat, stavu řádků a informace o verzi řádku.</span><span class="sxs-lookup"><span data-stu-id="a010f-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="a010f-119">Hodnoty sloupce jsou přidány, pouze pokud odpovídá názvu sloupce a data typ není kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="a010f-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="a010f-120">Následující příklad kódu vytvoří klon **datovou sadu** a pak přidá řádky z původní **datovou sadu** k **zákazníkům** tabulku v **datové sady**  klonování pro zákazníky, kde **země** sloupec má hodnotu "Germany".</span><span class="sxs-lookup"><span data-stu-id="a010f-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a010f-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a010f-121">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="a010f-122">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="a010f-122">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="a010f-123">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="a010f-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
