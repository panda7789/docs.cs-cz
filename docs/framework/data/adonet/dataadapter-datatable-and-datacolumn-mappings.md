---
title: DataAdapter DataTable a DataColumn mapování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 1b426dbcdc78ecfddeac003616993849ce60b89c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="9acd9-102">DataAdapter DataTable a DataColumn mapování</span><span class="sxs-lookup"><span data-stu-id="9acd9-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="9acd9-103">A **DataAdapter** obsahuje kolekci nula nebo více <xref:System.Data.Common.DataTableMapping> objekty v jeho **vlastnosti TableMappings** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9acd9-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="9acd9-104">A **DataTableMapping** poskytuje hlavní mapování mezi data vrácená z dotazu proti zdroji dat a <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="9acd9-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="9acd9-105">**DataTableMapping** název lze předat místě **DataTable** názvem k **vyplnění** metodu **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="9acd9-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="9acd9-106">Následující příklad vytvoří **DataTableMapping** s názvem **AuthorsMapping** pro **autoři** tabulky.</span><span class="sxs-lookup"><span data-stu-id="9acd9-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="9acd9-107">A **DataTableMapping** vám umožní použít názvy sloupců v **DataTable** , se liší od těch v databázi.</span><span class="sxs-lookup"><span data-stu-id="9acd9-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="9acd9-108">**DataAdapter** používá mapování tak, aby odpovídaly sloupce při aktualizaci tabulky.</span><span class="sxs-lookup"><span data-stu-id="9acd9-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="9acd9-109">Pokud nezadáte **TableName** nebo **DataTableMapping** název při volání metody **vyplnění** nebo **aktualizace** metodu  **DataAdapter**, **DataAdapter** vyhledává **DataTableMapping** s názvem "Tabulka".</span><span class="sxs-lookup"><span data-stu-id="9acd9-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="9acd9-110">Pokud tento **DataTableMapping** neexistuje, **TableName** z **DataTable** je "Tabulka".</span><span class="sxs-lookup"><span data-stu-id="9acd9-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="9acd9-111">Můžete zadat výchozí **DataTableMapping** tak, že vytvoříte **DataTableMapping** s názvem "Tabulka".</span><span class="sxs-lookup"><span data-stu-id="9acd9-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="9acd9-112">Následující příklad kódu vytvoří **DataTableMapping** (z <xref:System.Data.Common> oboru názvů) a udělá z něj výchozí mapování pro zadaný **DataAdapter** zadáním názvu "Tabulky".</span><span class="sxs-lookup"><span data-stu-id="9acd9-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="9acd9-113">V příkladu mapuje sloupce z tabulky první ve výsledku dotazu ( **zákazníci** tabulky **Northwind** databáze) na sadu více uživatelsky přívětivých názvů v **zákazníků Northwind**  tabulky v <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="9acd9-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9acd9-114">Pro sloupce, které nejsou namapované je název sloupce ve zdroji dat použít.</span><span class="sxs-lookup"><span data-stu-id="9acd9-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
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
  
 <span data-ttu-id="9acd9-115">V situacích, pokročilejší, můžete rozhodnout, který má stejné **DataAdapter** pro podporu načítání různých tabulek s jinou mapování.</span><span class="sxs-lookup"><span data-stu-id="9acd9-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="9acd9-116">K tomu jednoduše přidejte další **DataTableMapping** objekty.</span><span class="sxs-lookup"><span data-stu-id="9acd9-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="9acd9-117">Když **vyplnění** metodě se předává instanci **datovou sadu** a **DataTableMapping** je název, pokud mapování se stejným názvem existuje, je použít; jinak hodnota  **DataTable** s, který se používá název.</span><span class="sxs-lookup"><span data-stu-id="9acd9-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="9acd9-118">Následující příklady vytváření **DataTableMapping** s názvem **zákazníci** a **DataTable** název **BizTalkSchema**.</span><span class="sxs-lookup"><span data-stu-id="9acd9-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="9acd9-119">V příkladu mapuje řádky vrácené příkazem SELECT k **BizTalkSchema** **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="9acd9-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
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
>  <span data-ttu-id="9acd9-120">Pokud není zadaný název zdrojového sloupce pro mapování sloupců nebo názvu zdrojové tabulky není součástí pro mapování tabulky, budou automaticky generovány výchozí názvy.</span><span class="sxs-lookup"><span data-stu-id="9acd9-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="9acd9-121">Pokud je zdrojový sloupec zadaný pro mapování sloupců, mapování sloupců je zadána přírůstkové výchozí název **SourceColumn** *N,* počínaje **SourceColumn1**.</span><span class="sxs-lookup"><span data-stu-id="9acd9-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="9acd9-122">Pokud je zadaný žádný parametr názvu zdrojové tabulky pro mapování tabulky, mapování tabulky, je zadána přírůstkové výchozí název **SourceTable** *N*, od verze **SourceTable1**.</span><span class="sxs-lookup"><span data-stu-id="9acd9-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9acd9-123">Doporučujeme, abyste se zabránilo pojmenovávací konvenci **SourceColumn** *N* pro mapování sloupců, nebo **SourceTable** *N* pro tabulku mapování, protože název je zadat může dojít ke konfliktu s existujícím názvem mapování výchozí sloupec v **ColumnMappingCollection** nebo název tabulky mapování v **DataTableMappingCollection** .</span><span class="sxs-lookup"><span data-stu-id="9acd9-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="9acd9-124">Pokud se zadaným názvem již existuje, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="9acd9-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="9acd9-125">Zpracování více sad výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="9acd9-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="9acd9-126">Pokud vaše **SelectCommand** vrátí více tabulek, **vyplnění** automaticky vygeneruje názvy tabulek s přírůstkové hodnoty pro tabulky v **datovou sadu**, od verze Zadaný název tabulky a budete pokračovat na ve formě **TableName** *N*, od verze **TableName1**.</span><span class="sxs-lookup"><span data-stu-id="9acd9-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="9acd9-127">Mapování tabulky můžete použít k mapování názvu automaticky vytvářené tabulky název, který má zadaný pro tabulky **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="9acd9-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="9acd9-128">Například pro **SelectCommand** dvou tabulek, který vrací **zákazníci** a **objednávky**, vydávání následující volání **vyplnění**.</span><span class="sxs-lookup"><span data-stu-id="9acd9-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 <span data-ttu-id="9acd9-129">Dvě tabulky se vytváří v **datovou sadu**: **zákazníci** a **označena jako Zákazníci1**.</span><span class="sxs-lookup"><span data-stu-id="9acd9-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="9acd9-130">Mapování tabulky můžete použít k zajištění, že je v druhé tabulce s názvem **objednávky** místo **označena jako Zákazníci1**.</span><span class="sxs-lookup"><span data-stu-id="9acd9-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="9acd9-131">K tomuto účelu mapování zdrojové tabulky **označena jako Zákazníci1** k **datovou sadu** tabulky **objednávky**, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9acd9-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a><span data-ttu-id="9acd9-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="9acd9-132">See Also</span></span>  
 [<span data-ttu-id="9acd9-133">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="9acd9-133">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="9acd9-134">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9acd9-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="9acd9-135">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="9acd9-135">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
