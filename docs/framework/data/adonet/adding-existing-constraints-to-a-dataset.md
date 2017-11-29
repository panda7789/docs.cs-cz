---
title: "Přidání existující omezení datové sady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e457113eff471c620ccdbf78337d2013d7a62bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="adding-existing-constraints-to-a-dataset"></a><span data-ttu-id="863db-102">Přidání existující omezení datové sady</span><span class="sxs-lookup"><span data-stu-id="863db-102">Adding Existing Constraints to a DataSet</span></span>
<span data-ttu-id="863db-103">**Vyplnění** metodu **DataAdapter** doplní <xref:System.Data.DataSet> pouze se sloupci a řádky ze zdroje dat; tabulky ale omezení jsou běžně nastavit zdroj dat **vyplnění** metoda nepřidá tyto informace schématu **datovou sadu** ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="863db-103">The **Fill** method of the **DataAdapter** fills a <xref:System.Data.DataSet> only with table columns and rows from a data source; though constraints are commonly set by the data source, the **Fill** method does not add this schema information to the **DataSet** by default.</span></span> <span data-ttu-id="863db-104">K naplnění **datovou sadu** s stávající informace o omezení primárního klíče ze zdroje dat, můžete buď volání **FillSchema** metodu **DataAdapter**, nebo nastavte **MissingSchemaAction** vlastnost **DataAdapter** k **AddWithKey** před voláním **vyplnění**.</span><span class="sxs-lookup"><span data-stu-id="863db-104">To populate a **DataSet** with existing primary key constraint information from a data source, you can either call the **FillSchema** method of the **DataAdapter**, or set the **MissingSchemaAction** property of the **DataAdapter** to **AddWithKey** before calling **Fill**.</span></span> <span data-ttu-id="863db-105">Tím bude zajištěno, že primární klíč omezení **datovou sadu** odrážejí hodnoty ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="863db-105">This will ensure that primary key constraints in the **DataSet** reflect those at the data source.</span></span> <span data-ttu-id="863db-106">Informace o omezení cizího klíče nezahrnuje a musí být vytvořen explicitně, jak je znázorněno v [DataTable omezení](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="863db-106">Foreign key constraint information is not included and must be created explicitly, as shown in [DataTable Constraints](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="863db-107">Informace o schématu pro přidání **datovou sadu** před naplňování daty zajišťuje, aby byly součástí omezení primárního klíče <xref:System.Data.DataTable> objekty v **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="863db-107">Adding schema information to a **DataSet** before filling it with data ensures that primary key constraints are included with the <xref:System.Data.DataTable> objects in the **DataSet**.</span></span> <span data-ttu-id="863db-108">V důsledku toho, pokud další volání k vyplnění **datovou sadu** probíhají primární klíčový sloupec informace slouží tak, aby odpovídala nové záznamy ze zdroje dat s aktuální řádky v každé **DataTable**a aktuální data v v tabulkách se přepíše daty ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="863db-108">As a result, when additional calls to fill the **DataSet** are made, the primary key column information is used to match new rows from the data source with current rows in each **DataTable**, and current data in the tables is overwritten with data from the data source.</span></span> <span data-ttu-id="863db-109">Bez informace o schématu nové záznamy ze zdroje dat se připojí k **datovou sadu**, což je duplicitní řádky.</span><span class="sxs-lookup"><span data-stu-id="863db-109">Without the schema information, the new rows from the data source are appended to the **DataSet**, resulting in duplicate rows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="863db-110">Pokud se identifikuje sloupce ve zdroji dat jako automatické zvyšování **FillSchema** metody nebo **vyplnění** metoda s **MissingSchemaAction** z  **AddWithKey**, vytvoří **DataColumn** s **AutoIncrement** vlastnost nastavena na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="863db-110">If a column in a data source is identified as auto-incrementing, the **FillSchema** method, or the **Fill** method with a **MissingSchemaAction** of **AddWithKey**, creates a **DataColumn** with an **AutoIncrement** property set to `true`.</span></span> <span data-ttu-id="863db-111">Nicméně, budete muset nastavit **AutoIncrementStep** a **AutoIncrementSeed** hodnoty sami.</span><span class="sxs-lookup"><span data-stu-id="863db-111">However, you will need to set the **AutoIncrementStep** and **AutoIncrementSeed** values yourself.</span></span> <span data-ttu-id="863db-112">Další informace o automatické zvyšování sloupce najdete v tématu [vytváření sloupců AutoIncrement](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).</span><span class="sxs-lookup"><span data-stu-id="863db-112">For more information about auto-incrementing columns, see [Creating AutoIncrement Columns](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).</span></span>  
  
 <span data-ttu-id="863db-113">Pomocí **FillSchema** nebo nastavení **MissingSchemaAction** k **AddWithKey** vyžaduje další zpracování ve zdroji dat, které podávají informace sloupec primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="863db-113">Using **FillSchema** or setting the **MissingSchemaAction** to **AddWithKey** requires extra processing at the data source to determine primary key column information.</span></span> <span data-ttu-id="863db-114">Další zpracování může bránit ve výkonu.</span><span class="sxs-lookup"><span data-stu-id="863db-114">This additional processing can hinder performance.</span></span> <span data-ttu-id="863db-115">Pokud znáte primární informace o klíči v době návrhu, doporučujeme vám, že explicitně zadáte sloupec primárního klíče nebo sloupce pro dosažení optimálního výkonu.</span><span class="sxs-lookup"><span data-stu-id="863db-115">If you know the primary key information at design time, we recommend that you explicitly specify the primary key column or columns in order to achieve optimal performance.</span></span> <span data-ttu-id="863db-116">Informace o explicitně nastavení primární informace o klíči pro tabulku najdete v tématu [definování primárních klíčů](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="863db-116">For information about explicitly setting primary key information for a table, see [Defining Primary Keys](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="863db-117">Následující příklad kódu ukazuje, jak přidat informace o schématu pro **datovou sadu** pomocí **FillSchema**.</span><span class="sxs-lookup"><span data-stu-id="863db-117">The following code example shows how to add schema information to a **DataSet** using **FillSchema**.</span></span>  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 <span data-ttu-id="863db-118">Následující příklad kódu ukazuje, jak přidat informace o schématu pro **datovou sadu** pomocí **MissingSchemaAction.AddWithKey** vlastnost **vyplnění** metoda.</span><span class="sxs-lookup"><span data-stu-id="863db-118">The following code example shows how to add schema information to a **DataSet** using the **MissingSchemaAction.AddWithKey** property of the **Fill** method.</span></span>  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="863db-119">Zpracování více sad výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="863db-119">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="863db-120">Pokud **DataAdapter** zaznamená více sad výsledků dotazu vrácená z **SelectCommand**, vytvoří několik tabulek v **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="863db-120">If the **DataAdapter** encounters multiple result sets returned from the **SelectCommand**, it will create multiple tables in the **DataSet**.</span></span> <span data-ttu-id="863db-121">V tabulkách přidělí nule přírůstkové výchozí název **tabulky** *N*, od verze **tabulky** místo "Table0".</span><span class="sxs-lookup"><span data-stu-id="863db-121">The tables will be given a zero-based incremental default name of **Table** *N*, starting with **Table** instead of "Table0".</span></span> <span data-ttu-id="863db-122">Pokud je název tabulky předat jako argument k **FillSchema** metody tabulky přidělí nule přírůstkové název **TableName** *N*, od verze **TableName** místo "TableName0".</span><span class="sxs-lookup"><span data-stu-id="863db-122">If a table name is passed as an argument to the **FillSchema** method, the tables will be given a zero-based incremental name of **TableName** *N*, starting with **TableName** instead of "TableName0".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="863db-123">Pokud **FillSchema** metodu **třídy OleDbDataAdapter** objektu se říká pro příkaz, který vrátí více sad výsledků dotazu, je vrácena pouze informace o schématu z první sadu výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="863db-123">If the **FillSchema** method of the **OleDbDataAdapter** object is called for a command that returns multiple result sets, only the schema information from the first result set is returned.</span></span> <span data-ttu-id="863db-124">Při vrácení informací o schématu pro více výsledek nastaví pomocí **třídy OleDbDataAdapter**, doporučuje se, zda jste zadali **MissingSchemaAction** z **AddWithKey** a získat informace o schématu při volání metody **vyplnění** metoda.</span><span class="sxs-lookup"><span data-stu-id="863db-124">When returning schema information for multiple result sets using the **OleDbDataAdapter**, it is recommended that you specify a **MissingSchemaAction** of **AddWithKey** and obtain the schema information when calling the **Fill** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="863db-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="863db-125">See Also</span></span>  
 [<span data-ttu-id="863db-126">DataAdapters a DataReaders</span><span class="sxs-lookup"><span data-stu-id="863db-126">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="863db-127">Datové sady, DataTables a DataView</span><span class="sxs-lookup"><span data-stu-id="863db-127">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="863db-128">Načítání a upravovat Data v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="863db-128">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="863db-129">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="863db-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
