---
title: Kopírování obsahu datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: f60ef817773b6234b19856bfc0727eedb67e113e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205173"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="a6444-102">Kopírování obsahu datové sady</span><span class="sxs-lookup"><span data-stu-id="a6444-102">Copying DataSet Contents</span></span>
<span data-ttu-id="a6444-103">Můžete vytvořit kopii <xref:System.Data.DataSet> , abyste mohli pracovat s daty bez ovlivnění původních dat nebo pracovat s podmnožinou dat z **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="a6444-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="a6444-104">Když kopírujete **datovou sadu**, můžete:</span><span class="sxs-lookup"><span data-stu-id="a6444-104">When copying a **DataSet**, you can:</span></span>  
  
- <span data-ttu-id="a6444-105">Vytvořte přesnou kopii **datové sady**, včetně schématu, dat, informací o stavu řádku a verze řádků.</span><span class="sxs-lookup"><span data-stu-id="a6444-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
- <span data-ttu-id="a6444-106">Vytvořte **datovou sadu** , která obsahuje schéma existující **datové sady**, ale pouze řádky, které byly změněny.</span><span class="sxs-lookup"><span data-stu-id="a6444-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="a6444-107">Můžete vrátit všechny řádky, které byly změněny, nebo zadat konkrétní **nezměněnou DataRowState**.</span><span class="sxs-lookup"><span data-stu-id="a6444-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="a6444-108">Další informace o stavech řádků najdete v tématu [stavy řádků a verze řádků](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="a6444-108">For more information about row states, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
- <span data-ttu-id="a6444-109">Zkopírujte schéma nebo relační strukturu pouze pro **datovou sadu** bez kopírování řádků.</span><span class="sxs-lookup"><span data-stu-id="a6444-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="a6444-110">Řádky lze importovat do existujícího <xref:System.Data.DataTable> objektu using. <xref:System.Data.DataTable.ImportRow%2A></span><span class="sxs-lookup"><span data-stu-id="a6444-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="a6444-111">Chcete-li vytvořit přesnou kopii **datové sady** , která obsahuje schéma i data, použijte <xref:System.Data.DataSet.Copy%2A> metodu **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="a6444-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="a6444-112">Následující příklad kódu ukazuje, jak vytvořit přesnou kopii **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="a6444-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="a6444-113">Chcete-li vytvořit kopii **datové sady** , která obsahuje schéma a pouze data představující **přidané**, **upravené**nebo odstraněné řádky, použijte <xref:System.Data.DataSet.GetChanges%2A> metodu **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="a6444-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="a6444-114">Pomocí GetChanges můžete také vracet pouze řádky se zadaným stavem řádku předáním hodnoty **nezměněnou DataRowState** při volání metody GetChanges.</span><span class="sxs-lookup"><span data-stu-id="a6444-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="a6444-115">Následující příklad kódu ukazuje, jak předat **nezměněnou DataRowState** při volání metody GetChanges.</span><span class="sxs-lookup"><span data-stu-id="a6444-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
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
  
 <span data-ttu-id="a6444-116">Chcete-li vytvořit kopii **datové sady** , která obsahuje pouze schéma, použijte <xref:System.Data.DataSet.Clone%2A> metodu **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="a6444-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="a6444-117">Můžete také přidat existující řádky do klonované **datové sady** pomocí metody **ImportRow** **objektu DataTable**.</span><span class="sxs-lookup"><span data-stu-id="a6444-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="a6444-118">**ImportRow** přidá informace o datech, stavu řádků a verzi řádku do zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="a6444-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="a6444-119">Hodnoty sloupců jsou přidány pouze tam, kde se shodují název sloupce a datový typ je kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="a6444-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="a6444-120">Následující příklad kódu vytvoří klon **datové sady** a potom přidá řádky z původní **datové sady** do tabulky Customers ( **zákazníci** ) ve klonu **datové sady** pro zákazníky, kde sloupec **země** má hodnotu "Německo". ".</span><span class="sxs-lookup"><span data-stu-id="a6444-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a6444-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6444-121">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="a6444-122">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="a6444-122">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="a6444-123">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="a6444-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
