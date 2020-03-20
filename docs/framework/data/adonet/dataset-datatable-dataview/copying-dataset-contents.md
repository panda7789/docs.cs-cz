---
title: Kopírování obsahu datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: de13e07eb5c19b8beffa724fec4a128c418a4fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151361"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="e42ec-102">Kopírování obsahu datové sady</span><span class="sxs-lookup"><span data-stu-id="e42ec-102">Copying DataSet Contents</span></span>
<span data-ttu-id="e42ec-103">Můžete vytvořit kopii, <xref:System.Data.DataSet> takže můžete pracovat s daty bez ovlivnění původních dat, nebo pracovat s podmnožinou dat z **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="e42ec-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="e42ec-104">Při kopírování **datové sady**můžete:</span><span class="sxs-lookup"><span data-stu-id="e42ec-104">When copying a **DataSet**, you can:</span></span>  
  
- <span data-ttu-id="e42ec-105">Vytvořte přesnou kopii **dataset**, včetně schématu, data, informace o stavu řádku a verze řádků.</span><span class="sxs-lookup"><span data-stu-id="e42ec-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
- <span data-ttu-id="e42ec-106">Vytvořte **datovou sadu,** která obsahuje schéma existující **dataset**, ale pouze řádky, které byly změněny.</span><span class="sxs-lookup"><span data-stu-id="e42ec-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="e42ec-107">Můžete vrátit všechny řádky, které byly změněny, nebo zadat konkrétní **DataRowState**.</span><span class="sxs-lookup"><span data-stu-id="e42ec-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="e42ec-108">Další informace o stavech řádků naleznete v [tématu Stavy řádků a Verze řádků](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="e42ec-108">For more information about row states, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
- <span data-ttu-id="e42ec-109">Zkopírujte schéma nebo relační strukturu pouze **DataSet,** bez kopírování řádků.</span><span class="sxs-lookup"><span data-stu-id="e42ec-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="e42ec-110">Řádky lze importovat do <xref:System.Data.DataTable> <xref:System.Data.DataTable.ImportRow%2A>existující pomocí .</span><span class="sxs-lookup"><span data-stu-id="e42ec-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="e42ec-111">Chcete-li vytvořit přesnou kopii **dataset,** který obsahuje schéma <xref:System.Data.DataSet.Copy%2A> a data, použijte metodu **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="e42ec-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="e42ec-112">Následující příklad kódu ukazuje, jak vytvořit přesnou kopii **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="e42ec-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="e42ec-113">Chcete-li vytvořit kopii **datové sady,** která obsahuje schéma a pouze data představující řádky <xref:System.Data.DataSet.GetChanges%2A> **Přidané**, **Změněno**nebo **Odstraněno,** použijte metodu **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="e42ec-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="e42ec-114">Můžete také použít **GetChanges** vrátit pouze řádky se zadaným stavem řádku předáním **DataRowState** hodnotu při volání **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="e42ec-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="e42ec-115">Následující příklad kódu ukazuje, jak předat **DataRowState** při volání **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="e42ec-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
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
  
 <span data-ttu-id="e42ec-116">Chcete-li vytvořit kopii **dataset,** který obsahuje pouze <xref:System.Data.DataSet.Clone%2A> schéma, použijte metodu **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="e42ec-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="e42ec-117">Existující řádky můžete také přidat do klonované **datové sady** pomocí metody **ImportRow** **datatable**.</span><span class="sxs-lookup"><span data-stu-id="e42ec-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="e42ec-118">**ImportRow** přidá data, stav řádku a informace o verzi řádku do zadané tabulky.</span><span class="sxs-lookup"><span data-stu-id="e42ec-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="e42ec-119">Hodnoty sloupců jsou přidány pouze tam, kde se název sloupce shoduje a datový typ je kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="e42ec-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="e42ec-120">Následující příklad kódu vytvoří klon **DataSet** a potom přidá řádky z původní **dataset** do tabulky **Zákazníci** v **dataset** klon pro zákazníky, kde sloupec **Země** má hodnotu "Německo".</span><span class="sxs-lookup"><span data-stu-id="e42ec-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e42ec-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="e42ec-121">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="e42ec-122">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="e42ec-122">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="e42ec-123">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e42ec-123">ADO.NET Overview</span></span>](../ado-net-overview.md)
