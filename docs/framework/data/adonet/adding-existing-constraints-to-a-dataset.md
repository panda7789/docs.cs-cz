---
title: Přidání existujících omezení do datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: 90aa1e5dceb3cac87d330837496b9dc467dc1876
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555469"
---
# <a name="adding-existing-constraints-to-a-dataset"></a><span data-ttu-id="7cefc-102">Přidání existujících omezení do datové sady</span><span class="sxs-lookup"><span data-stu-id="7cefc-102">Adding Existing Constraints to a DataSet</span></span>
<span data-ttu-id="7cefc-103">**Vyplnit** metodu **DataAdapter** vyplní <xref:System.Data.DataSet> jenom pomocí sloupce tabulky a řádky ze zdroje dat, i když omezení běžně nastavené ve zdroji dat **vyplnit** metoda nepřidá informace o tomto schématu **datovou sadu** ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="7cefc-103">The **Fill** method of the **DataAdapter** fills a <xref:System.Data.DataSet> only with table columns and rows from a data source; though constraints are commonly set by the data source, the **Fill** method does not add this schema information to the **DataSet** by default.</span></span> <span data-ttu-id="7cefc-104">K naplnění **datovou sadu** s stávající informace o omezení primárního klíče ze zdroje dat, můžete buď zavolat **FillSchema** metodu **DataAdapter**, nebo nastavte **MissingSchemaAction** vlastnost **DataAdapter** k **AddWithKey** před voláním **vyplnit**.</span><span class="sxs-lookup"><span data-stu-id="7cefc-104">To populate a **DataSet** with existing primary key constraint information from a data source, you can either call the **FillSchema** method of the **DataAdapter**, or set the **MissingSchemaAction** property of the **DataAdapter** to **AddWithKey** before calling **Fill**.</span></span> <span data-ttu-id="7cefc-105">To zajistí, že primární klíče omezení **datovou sadu** odrážejí hodnoty ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="7cefc-105">This will ensure that primary key constraints in the **DataSet** reflect those at the data source.</span></span> <span data-ttu-id="7cefc-106">Informace o omezení pro cizí klíč nezahrnuje a musí být vytvořen explicitně, jak je znázorněno v [omezení datových tabulek](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="7cefc-106">Foreign key constraint information is not included and must be created explicitly, as shown in [DataTable Constraints](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="7cefc-107">Přidání informací o schématu pro **datovou sadu** před naplňování daty zajistí, že jsou součástí omezení primárního klíče <xref:System.Data.DataTable> objekty v **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="7cefc-107">Adding schema information to a **DataSet** before filling it with data ensures that primary key constraints are included with the <xref:System.Data.DataTable> objects in the **DataSet**.</span></span> <span data-ttu-id="7cefc-108">V důsledku toho při dalších volání tak, aby vyplnil **datovou sadu** probíhají primární informace o sloupci klíče se používá tak, aby odpovídala nové řádky ze zdroje dat s aktuální řádky v každém **DataTable**a aktuální data s daty ze zdroje dat je přepsán v tabulkách.</span><span class="sxs-lookup"><span data-stu-id="7cefc-108">As a result, when additional calls to fill the **DataSet** are made, the primary key column information is used to match new rows from the data source with current rows in each **DataTable**, and current data in the tables is overwritten with data from the data source.</span></span> <span data-ttu-id="7cefc-109">Bez informace o schématu, nových řádků ze zdroje dat jsou připojeny k **datovou sadu**výsledkem duplicitní řádky.</span><span class="sxs-lookup"><span data-stu-id="7cefc-109">Without the schema information, the new rows from the data source are appended to the **DataSet**, resulting in duplicate rows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7cefc-110">Pokud sloupce ve zdroji dat se identifikuje jako automatické zvyšování **FillSchema** metodu, nebo **vyplnit** metodou **MissingSchemaAction** z  **AddWithKey**, vytvoří **DataColumn** s **AutoIncrement** nastavenou na `true`.</span><span class="sxs-lookup"><span data-stu-id="7cefc-110">If a column in a data source is identified as auto-incrementing, the **FillSchema** method, or the **Fill** method with a **MissingSchemaAction** of **AddWithKey**, creates a **DataColumn** with an **AutoIncrement** property set to `true`.</span></span> <span data-ttu-id="7cefc-111">Ale budete muset nastavit **AutoIncrementStep** a **AutoIncrementSeed** hodnoty sami.</span><span class="sxs-lookup"><span data-stu-id="7cefc-111">However, you will need to set the **AutoIncrementStep** and **AutoIncrementSeed** values yourself.</span></span> <span data-ttu-id="7cefc-112">Další informace o automatické zvyšování sloupců, naleznete v tématu [vytváření sloupců s automatickým navyšováním](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).</span><span class="sxs-lookup"><span data-stu-id="7cefc-112">For more information about auto-incrementing columns, see [Creating AutoIncrement Columns](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).</span></span>  
  
 <span data-ttu-id="7cefc-113">Pomocí **FillSchema** nebo nastavení **MissingSchemaAction** k **AddWithKey** vyžaduje další zpracování na zdroj dat zjistit informace o sloupec primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="7cefc-113">Using **FillSchema** or setting the **MissingSchemaAction** to **AddWithKey** requires extra processing at the data source to determine primary key column information.</span></span> <span data-ttu-id="7cefc-114">Tato další zpracování může bránit výkonu.</span><span class="sxs-lookup"><span data-stu-id="7cefc-114">This additional processing can hinder performance.</span></span> <span data-ttu-id="7cefc-115">Pokud víte, informace o primárním klíči v době návrhu, doporučujeme, že explicitně neurčíte sloupec primárního klíče nebo sloupce, abyste dosáhli optimálního výkonu.</span><span class="sxs-lookup"><span data-stu-id="7cefc-115">If you know the primary key information at design time, we recommend that you explicitly specify the primary key column or columns in order to achieve optimal performance.</span></span> <span data-ttu-id="7cefc-116">Informace o explicitním nastavením informacemi o primárním klíči pro tabulku, naleznete v tématu [definování primárních klíčů](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="7cefc-116">For information about explicitly setting primary key information for a table, see [Defining Primary Keys](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="7cefc-117">Následující příklad kódu ukazuje, jak přidat informace o schématu **datovou sadu** pomocí **FillSchema**.</span><span class="sxs-lookup"><span data-stu-id="7cefc-117">The following code example shows how to add schema information to a **DataSet** using **FillSchema**.</span></span>  
  
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
  
 <span data-ttu-id="7cefc-118">Následující příklad kódu ukazuje, jak přidat informace o schématu **datovou sadu** pomocí **MissingSchemaAction.AddWithKey** vlastnost **vyplnit** metoda.</span><span class="sxs-lookup"><span data-stu-id="7cefc-118">The following code example shows how to add schema information to a **DataSet** using the **MissingSchemaAction.AddWithKey** property of the **Fill** method.</span></span>  
  
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
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="7cefc-119">Zpracování více sad výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="7cefc-119">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="7cefc-120">Pokud **DataAdapter** nalezne více sad výsledků dotazu vrácená **SelectCommand**, vytvoří více tabulek v **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="7cefc-120">If the **DataAdapter** encounters multiple result sets returned from the **SelectCommand**, it will create multiple tables in the **DataSet**.</span></span> <span data-ttu-id="7cefc-121">Tabulky dostanou od nuly přírůstkové výchozí název **tabulky** *N*počínaje **tabulky** namísto "Table0".</span><span class="sxs-lookup"><span data-stu-id="7cefc-121">The tables will be given a zero-based incremental default name of **Table** *N*, starting with **Table** instead of "Table0".</span></span> <span data-ttu-id="7cefc-122">Pokud zadáte název tabulky je předán jako argument **FillSchema** metody tabulky dostanou od nuly přírůstkové název **TableName** *N*počínaje **TableName** namísto "TableName0".</span><span class="sxs-lookup"><span data-stu-id="7cefc-122">If a table name is passed as an argument to the **FillSchema** method, the tables will be given a zero-based incremental name of **TableName** *N*, starting with **TableName** instead of "TableName0".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7cefc-123">Pokud **FillSchema** metodu **objektu OleDbDataAdapter** objektu je volána pro příkaz, který vrátí více sad výsledků dotazu, se vrátí jenom informace o schématu z první sady výsledků.</span><span class="sxs-lookup"><span data-stu-id="7cefc-123">If the **FillSchema** method of the **OleDbDataAdapter** object is called for a command that returns multiple result sets, only the schema information from the first result set is returned.</span></span> <span data-ttu-id="7cefc-124">Při vrácení informací o schématu pro více výsledku nastaví pomocí **objektu OleDbDataAdapter**, doporučuje se, že zadáte **MissingSchemaAction** z **AddWithKey** a získat informace o schématu při volání **vyplnit** metody.</span><span class="sxs-lookup"><span data-stu-id="7cefc-124">When returning schema information for multiple result sets using the **OleDbDataAdapter**, it is recommended that you specify a **MissingSchemaAction** of **AddWithKey** and obtain the schema information when calling the **Fill** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cefc-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="7cefc-125">See Also</span></span>  
 [<span data-ttu-id="7cefc-126">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="7cefc-126">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="7cefc-127">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="7cefc-127">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="7cefc-128">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7cefc-128">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="7cefc-129">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="7cefc-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
