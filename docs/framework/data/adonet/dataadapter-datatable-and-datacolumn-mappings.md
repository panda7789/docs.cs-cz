---
title: Mapování adaptéru dat, datové tabulky a datového sloupce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 54af7c2f449f8eb289841fb3eca357c6916404aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032692"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="b2c01-102">Mapování adaptéru dat, datové tabulky a datového sloupce</span><span class="sxs-lookup"><span data-stu-id="b2c01-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="b2c01-103">A **DataAdapter** obsahuje kolekci nula nebo více <xref:System.Data.Common.DataTableMapping> objekty v jeho **TableMappings** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b2c01-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="b2c01-104">A **DataTableMapping** poskytuje hlavní mapování mezi data vrácená z dotazu na zdroji dat a <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="b2c01-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="b2c01-105">**DataTableMapping** název mohou být předány místo **DataTable** název k **vyplnit** metodu **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="b2c01-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="b2c01-106">Následující příklad vytvoří **DataTableMapping** s názvem **AuthorsMapping** pro **autoři** tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2c01-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="b2c01-107">A **DataTableMapping** vám umožní použít názvy sloupců **DataTable** , která se liší od těch, které v databázi.</span><span class="sxs-lookup"><span data-stu-id="b2c01-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="b2c01-108">**DataAdapter** používá mapování tak, aby odpovídaly sloupce, když dojde k aktualizaci tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2c01-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="b2c01-109">Pokud nezadáte **TableName** nebo **DataTableMapping** pojmenujte při volání **vyplnit** nebo **aktualizace** metodu  **Vlastnost DataAdapter**, **DataAdapter** vyhledá **DataTableMapping** s názvem "Table".</span><span class="sxs-lookup"><span data-stu-id="b2c01-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="b2c01-110">Pokud to **DataTableMapping** buď neexistuje, **TableName** z **DataTable** je "Table".</span><span class="sxs-lookup"><span data-stu-id="b2c01-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="b2c01-111">Můžete určit výchozí **DataTableMapping** tak, že vytvoříte **DataTableMapping** s názvem "Table".</span><span class="sxs-lookup"><span data-stu-id="b2c01-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="b2c01-112">Následující příklad kódu vytvoří **DataTableMapping** (z <xref:System.Data.Common> oboru názvů) a zpřístupňuje je výchozí mapování pro zadaný rozbočovač **DataAdapter** zadáním názvu "Table".</span><span class="sxs-lookup"><span data-stu-id="b2c01-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="b2c01-113">V příkladu pak namapuje sloupce z první tabulky ve výsledku dotazu ( **zákazníkům** tabulku **Northwind** databáze) na sadu přívětivější názvy v **zákazníků Northwind**  v tabulku <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b2c01-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b2c01-114">Název sloupce ze zdroje dat se používá u sloupců, které nejsou namapované.</span><span class="sxs-lookup"><span data-stu-id="b2c01-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
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
  
 <span data-ttu-id="b2c01-115">V rozšířené situacích může rozhodnout, který má stejný **DataAdapter** nepodporuje načtení různých tabulek s jinou mapování.</span><span class="sxs-lookup"><span data-stu-id="b2c01-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="b2c01-116">K tomu jednoduše přidejte další **DataTableMapping** objekty.</span><span class="sxs-lookup"><span data-stu-id="b2c01-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="b2c01-117">Při **vyplnit** metodě je předána instance **datovou sadu** a **DataTableMapping** název, pokud se mapování s tímto názvem existuje, je použít jinak  **Objekt DataTable** s, který se používá název.</span><span class="sxs-lookup"><span data-stu-id="b2c01-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="b2c01-118">Následující příklady vytváří **DataTableMapping** s názvem **zákazníkům** a **DataTable** název **BizTalkSchema**.</span><span class="sxs-lookup"><span data-stu-id="b2c01-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="b2c01-119">V příkladu pak namapuje řádky vrácené příkazu SELECT **BizTalkSchema** **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="b2c01-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
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
>  <span data-ttu-id="b2c01-120">Pokud není zadán název zdrojového sloupce pro mapování sloupců nebo není zadán název tabulky zdrojového mapování tabulky, budou automaticky generovány výchozími názvy.</span><span class="sxs-lookup"><span data-stu-id="b2c01-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="b2c01-121">Pokud žádný zdrojový sloupec je zadán pro mapování sloupců, mapování sloupců je předána přírůstkové výchozí název **SourceColumn** *N,* počínaje **SourceColumn1**.</span><span class="sxs-lookup"><span data-stu-id="b2c01-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="b2c01-122">Pokud název tabulky žádný zdroj není zadána pro mapování tabulky, mapování tabulek je předána přírůstkové výchozí název **SourceTable** *N*počínaje **SourceTable1**.</span><span class="sxs-lookup"><span data-stu-id="b2c01-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2c01-123">Doporučujeme vám, že byste se vyhnout zásadu vytváření názvů **SourceColumn** *N* pro mapování sloupců, nebo **SourceTable** *N* pro tabulku vzhledem k tomu, že zadáte název dojít ke konfliktu s existujícím názvem mapování výchozí sloupce v mapování **ColumnMappingCollection** nebo název mapování tabulky v **DataTableMappingCollection** .</span><span class="sxs-lookup"><span data-stu-id="b2c01-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="b2c01-124">Pokud zadaný název již existuje, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="b2c01-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="b2c01-125">Zpracování více sad výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="b2c01-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="b2c01-126">Pokud vaše **SelectCommand** vrátí více tabulek, **vyplnit** automaticky vygeneruje názvy tabulek s přírůstkové hodnoty pro tabulky v **datovou sadu**počínaje Zadaný název tabulky a pokračuje na ve formě **TableName** *N*počínaje **TableName1**.</span><span class="sxs-lookup"><span data-stu-id="b2c01-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="b2c01-127">Mapování tabulek můžete použít k mapování názvu automaticky vytvářené tabulky na název, který má zadané pro tabulku v **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="b2c01-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="b2c01-128">Třeba **SelectCommand** dvou tabulek, který vrací **zákazníkům** a **objednávky**, vydat následující volání do **vyplnit**.</span><span class="sxs-lookup"><span data-stu-id="b2c01-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 <span data-ttu-id="b2c01-129">Dvě tabulky vytvářejí **datovou sadu**: **Zákazníci** a **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="b2c01-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="b2c01-130">Mapování tabulek můžete použít k zajištění, že je v druhé tabulce s názvem **objednávky** místo **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="b2c01-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="b2c01-131">K tomuto účelu mapování zdrojové tabulky **Customers1** k **datovou sadu** tabulky **objednávky**, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b2c01-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2c01-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2c01-132">See also</span></span>

- [<span data-ttu-id="b2c01-133">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="b2c01-133">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="b2c01-134">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b2c01-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="b2c01-135">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="b2c01-135">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
