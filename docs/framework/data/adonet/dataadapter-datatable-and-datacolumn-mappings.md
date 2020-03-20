---
title: Mapování adaptéru dat, datové tabulky a datového sloupce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 6380dd0512bd7834f50b87f90f445cb01b7a8b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151556"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="d66c4-102">Mapování adaptéru dat, datové tabulky a datového sloupce</span><span class="sxs-lookup"><span data-stu-id="d66c4-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="d66c4-103">A **DataAdapter** obsahuje kolekci <xref:System.Data.Common.DataTableMapping> nula nebo více objektů v jeho **TableMappings** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d66c4-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="d66c4-104">A **DataTableMapping** poskytuje hlavní mapování mezi daty vrácená z <xref:System.Data.DataTable>dotazu proti zdroji dat a .</span><span class="sxs-lookup"><span data-stu-id="d66c4-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="d66c4-105">Název **DataTableMapping** může být předán místo názvu **DataTable** metodě **Fill** **dataadapter**.</span><span class="sxs-lookup"><span data-stu-id="d66c4-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="d66c4-106">Následující příklad vytvoří **datatablemapping** s názvem **AuthorsMapping** pro tabulku **Autoři.**</span><span class="sxs-lookup"><span data-stu-id="d66c4-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="d66c4-107">A **DataTableMapping** umožňuje používat názvy sloupců v **DataTable,** které se liší od těch v databázi.</span><span class="sxs-lookup"><span data-stu-id="d66c4-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="d66c4-108">**DataAdapter** používá mapování tak, aby odpovídalo sloupcům při aktualizaci tabulky.</span><span class="sxs-lookup"><span data-stu-id="d66c4-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="d66c4-109">Pokud při volání metody **Fill** nebo **Update** **datového adaptéru**nezadáte název **TableName** nebo **DataTableMapping** , **hledá dataadapter** **datatablemapping** s názvem "Tabulka".</span><span class="sxs-lookup"><span data-stu-id="d66c4-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="d66c4-110">Pokud **toto mapování DataTableMapping** neexistuje, **název_tabulky** **tabulka** je "Tabulka".</span><span class="sxs-lookup"><span data-stu-id="d66c4-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="d66c4-111">Výchozí **mapování datatablemapping** můžete zadat vytvořením **datatablemappingu** s názvem "Tabulka".</span><span class="sxs-lookup"><span data-stu-id="d66c4-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="d66c4-112">Následující příklad kódu vytvoří **datatablemapping** <xref:System.Data.Common> (z oboru názvů) a znějí výchozím mapováním pro zadaný **adaptér DataAdapter** pojmenováním "Tabulka".</span><span class="sxs-lookup"><span data-stu-id="d66c4-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="d66c4-113">Příklad pak mapuje sloupce z první tabulky ve výsledku dotazu (tabulka **Zákazníci** databáze **Northwind)** na sadu uživatelsky <xref:System.Data.DataSet>přívětivějších názvů v tabulce **Zákazníci Northwind** v tabulce .</span><span class="sxs-lookup"><span data-stu-id="d66c4-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="d66c4-114">Pro sloupce, které nejsou mapovány, se používá název sloupce ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="d66c4-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
```  
  
```csharp  
DataTableMapping mapping =
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 <span data-ttu-id="d66c4-115">V pokročilejších situacích se můžete rozhodnout, že chcete, aby stejný **adaptér DataAdapter** podporoval načítání různých tabulek s různými mapováními.</span><span class="sxs-lookup"><span data-stu-id="d66c4-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="d66c4-116">Chcete-li to provést, jednoduše přidejte další objekty **DataTableMapping.**</span><span class="sxs-lookup"><span data-stu-id="d66c4-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="d66c4-117">Když **fill** metoda je předána instance **DataSet** a **DataTableMapping** název, pokud mapování s tímto názvem existuje, že se používá; v opačném případě je **použita datatable** s tímto názvem.</span><span class="sxs-lookup"><span data-stu-id="d66c4-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="d66c4-118">Následující příklady vytvořit **DataTableMapping** s názvem **zákazníci** a **DataTable** název **BizTalkSchema**.</span><span class="sxs-lookup"><span data-stu-id="d66c4-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="d66c4-119">Příklad pak mapuje řádky vrácené příkazem SELECT na **BizTalkSchema** **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="d66c4-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
ITableMapping mapping =
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
> <span data-ttu-id="d66c4-120">Pokud pro mapování sloupců není zadán název zdrojového sloupce nebo není zadán název zdrojové tabulky pro mapování tabulky, budou automaticky generovány výchozí názvy.</span><span class="sxs-lookup"><span data-stu-id="d66c4-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="d66c4-121">Pokud pro mapování sloupců není zadán žádný zdrojový sloupec, je mapování sloupců přidělen o zdrojový výchozí název **SourceColumn** *N,* počínaje **SourceColumn1**.</span><span class="sxs-lookup"><span data-stu-id="d66c4-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="d66c4-122">Pokud pro mapování tabulky není zadán žádný název zdrojové tabulky, je mapování tabulky přidělen o zdrojový výchozí název **Table N** *N*, počínaje **SourceTable1**.</span><span class="sxs-lookup"><span data-stu-id="d66c4-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d66c4-123">Doporučujeme vyhnout se konvenci pojmenování **SourceColumn** *N* pro mapování sloupců nebo **SourceTable** *N* pro mapování tabulky, protože název, který zadáte, může být v konfliktu s existujícím výchozím názvem mapování sloupců v **kolekci ColumnMappingCollection** nebo název mapování tabulky v **datatablemappingcollectioncollection**.</span><span class="sxs-lookup"><span data-stu-id="d66c4-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="d66c4-124">Pokud zadaný název již existuje, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d66c4-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="d66c4-125">Zpracování více sad výsledků</span><span class="sxs-lookup"><span data-stu-id="d66c4-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="d66c4-126">Pokud příkaz **SelectCommand** vrátí více tabulek, **funkce Fill** automaticky vygeneruje názvy tabulek s přírůstkovými hodnotami pro tabulky v **datové sadě**, počínaje zadaným názvem tabulky a pokračováním ve formuláři **TableName** *N*, počínaje **názvem TableName1**.</span><span class="sxs-lookup"><span data-stu-id="d66c4-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="d66c4-127">Mapování tabulek můžete použít k mapování automaticky generovaného názvu tabulky na název, který chcete zadat pro tabulku v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="d66c4-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="d66c4-128">Například pro **SelectCommand,** který vrací dvě tabulky, **Zákazníci** a **Objednávky**, vydat následující volání **Fill**.</span><span class="sxs-lookup"><span data-stu-id="d66c4-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 <span data-ttu-id="d66c4-129">Dvě tabulky jsou vytvořeny v **datové sadě**: **Zákazníci** a **Zákazníci1**.</span><span class="sxs-lookup"><span data-stu-id="d66c4-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="d66c4-130">Mapování tabulek můžete použít k zajištění, že druhá tabulka je s názvem **Objednávky** místo **Zákazníci1**.</span><span class="sxs-lookup"><span data-stu-id="d66c4-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="d66c4-131">Chcete-li to provést, namapujte zdrojovou tabulku **Zákazníci1** na **objednávky**tabulky **DataSet** , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d66c4-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a><span data-ttu-id="d66c4-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="d66c4-132">See also</span></span>

- [<span data-ttu-id="d66c4-133">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="d66c4-133">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="d66c4-134">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d66c4-134">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="d66c4-135">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d66c4-135">ADO.NET Overview</span></span>](ado-net-overview.md)
